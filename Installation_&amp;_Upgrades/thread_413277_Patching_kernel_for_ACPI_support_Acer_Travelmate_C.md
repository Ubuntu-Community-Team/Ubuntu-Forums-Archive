---
title: "Patching kernel for ACPI support Acer Travelmate C100"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Paradoxdruid on 2007-04-19
I finally got around to pulling my old Acer Travelmate C100 (an original Tablet PC!) out of storage and installing Kubuntu 6.10 on it, and it works like a charm, tablet functionality and all.

The problem is, the battery status doesn't work--  it says no battery is even connected.  I'm apparantly not the only person with this problem.  On the [Acer Travelmate C100 page on the Gentoo wiki]("http://gentoo-wiki.com/HARDWARE_Acer_Travelmate_C100#ACPI_support"), someone said:
> It was a hard fight to let the kernel accept ACPI support for my C100, it seems that its RSDP checksum is invalid and the kernel refuses to enable ACPI support because of this. Dean Townsley provided a patch forcing the kernel to use a more sophisticated routine to detect the ACPI data tables (it seems that there are two different functions existing) and voila - it works. **While Ubuntu 6.06's Live CD accounts for this ACPI problem, an actual installation remains ignorant of the matter.** (emphasis mine).  This is exactly what I encountered as well--  it worked on the Live CD, so I assumed it would on the install.

The patch they list to fix it is pretty short, but targeted against an older kernel.

What would be the easiest way to apply a similar fix to a 2.6.17 kernel?  I'm good enough at linux to follow the howtos (like [this one]("http://www.howtoforge.com/kernel_compilation_ubuntu")) to compile my own kernel, but not good enough to author a new diff file.

If anyone can help or has other ideas, I'd love to hear it.  Thank you!

---

### Post by Paradoxdruid on 2007-04-19
D'oh!  I forgot Feisty was coming out, and my message was doomed to be buried.  I'll bump it this once, and if nothing comes of it, try bumping it again in a week or so.

Thanks for any help!

---

### Post by Paradoxdruid on 2007-04-22
I did it!

I manually applied the patch that Dean Townsley wrote (from [the Gentoo Hardware Wiki]("http://gentoo-wiki.com/HARDWARE_Acer_Travelmate_C100#ACPI_support")) to the linux-source-2.6.20 from the Ubuntu repositories.

After making my kernel packages and installing them, it works like a charm-- now I see battery status, and I can control the dynamic CPU frequency changes.

So I turned my changes into a patch file to share with the community, attached below. 

> 
--- linux-source-2.6.20/arch/i386/kernel/acpi/boot.c 2007-04-12 10:15:46.000000000 -0700
+++ linux/arch/i386/kernel/acpi/boot.c 2007-04-22 10:21:34.000000000 -0700
@@ -600,24 +600,7 @@

EXPORT_SYMBOL(acpi_unregister_ioapic);

-static unsigned long __init
-acpi_scan_rsdp(unsigned long start, unsigned long length)
-{
- unsigned long offset = 0;
- unsigned long sig_len = sizeof("RSD PTR ") - 1;

- /*
- * Scan all 16-byte boundaries of the physical memory region for the
- * RSDP signature.
- */
- for (offset = 0; offset < length; offset += 16) {
- if (strncmp((char *)(phys_to_virt(start) + offset), "RSD PTR ", sig_len))
- continue;
- return (start + offset);
- }
-
- return 0;
-}

static int __init acpi_parse_sbf(unsigned long phys_addr, unsigned long size)
{
@@ -753,21 +736,11 @@

unsigned long __init acpi_find_rsdp(void)
{
+ struct acpi_pointer addr;
unsigned long rsdp_phys = 0;

- if (efi_enabled) {
- if (efi.acpi20 != EFI_INVALID_TABLE_ADDR)
- return efi.acpi20;
- else if (efi.acpi != EFI_INVALID_TABLE_ADDR)
- return efi.acpi;
- }
- /*
- * Scan memory looking for the RSDP signature. First search EBDA (low
- * memory) paragraphs and then search upper memory (E0000-FFFFF).
- */
- rsdp_phys = acpi_scan_rsdp(0, 0x400);
- if (!rsdp_phys)
- rsdp_phys = acpi_scan_rsdp(0xE0000, 0x20000);
+ if (!ACPI_FAILURE(acpi_find_root_pointer(ACPI_PHYSICAL_ADDRESSING,&addr)))
+ rsdp_phys=addr.pointer.physical;

return rsdp_phys;
}


--- linux-source-2.6.20/arch/i386/mach-es7000/es7000plat.c 2007-04-12 10:15:46.000000000 -0700
+++ linux/arch/i386/mach-es7000/es7000plat.c 2007-04-22 10:25:08.000000000 -0700
@@ -35,6 +35,7 @@
#include <linux/reboot.h>
#include <linux/init.h>
#include <linux/acpi.h>
+#include <linux/efi.h>
#include <asm/io.h>
#include <asm/nmi.h>
#include <asm/smp.h>
@@ -91,6 +92,52 @@
ioapic_renumber_irq = es7000_rename_gsi;
}

+
+ static unsigned long __init
+ es7000_acpi_scan_rsdp (
+ unsigned long start,
+ unsigned long length)
+ {
+ unsigned long offset = 0;
+ unsigned long sig_len = sizeof("RSD PTR ") - 1;
+
+ /*
+ * Scan all 16-byte boundaries of the physical memory region for the
+ * RSDP signature.
+ */
+ for (offset = 0; offset < length; offset += 16) {
+ if (strncmp((char *) (start + offset), "RSD PTR ", sig_len))
+ continue;
+ return (start + offset);
+ }
+
+ return 0;
+ }
+
+
+ unsigned long __init
+ es7000_acpi_find_rsdp (void)
+ {
+ unsigned long rsdp_phys = 0;
+
+ if (efi_enabled) {
+ if (efi.acpi20)
+ return __pa(efi.acpi20);
+ else if (efi.acpi)
+ return __pa(efi.acpi);
+ }
+ /*
+ * Scan memory looking for the RSDP signature. First search EBDA (low
+ * memory) paragraphs and then search upper memory (E0000-FFFFF).
+ */
+ rsdp_phys = es7000_acpi_scan_rsdp (0, 0x400);
+ if (!rsdp_phys)
+ rsdp_phys = es7000_acpi_scan_rsdp (0xE0000, 0xFFFFF);
+
+ return rsdp_phys;
+ }
+
+
/*
* Parse the OEM Table
*/
@@ -166,7 +213,8 @@
int i;
struct acpi_table_sdt sdt;

- rsdp_phys = acpi_find_rsdp();
+ /* FIXME -- can we use the general acpi_find_rsdp() ? */
+ rsdp_phys = es7000_acpi_find_rsdp();
rsdp = __va(rsdp_phys);
if (rsdp->rsdt_address) {
struct acpi_table_rsdt *mapped_rsdt = NULL;

Not really much work at all-- the only reason that Dean's patch wouldn't still work is that the context cues in his patch file aren't current enough for patch to deduce where to make the changes.

---

### Post by redpoint7 on 2007-04-29
Hi,

thx very much for sharing but could you help me please and tell me what I should do with this patch file?

executing it as a sh-file doesn't work and using it in the /usr/src/linux dir with:
cat patch-filename.diff | patch -p1 --dry-run
throws some errors.

I asume that I do something wrong with this patch-file and I have really no ideas what to do with it :-)
The gentoo wiki you refered to, asumes as well, that everyone knows what to do with this code ;-)

So I would be very grateful if someone could help me,
thx very much in advance

---

### Post by Paradoxdruid on 2007-04-29
Hi redpoint,

I used this guide extensively to know what I was doing:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

It explains how to unpack and set up kernel source, how to apply patches, how to make that into kernel packages, and how to install them on your system.

Hope it helps!

---

### Post by Paradoxdruid on 2007-04-29
Also, I didn't include the diff -ur lines in my patch, maybe they are needed.  Try this patch:

```
diff -ur linux-2.6.20/arch/i386/kernel/acpi/boot.c linux/arch/i386/kernel/acpi/boot.c
--- linux-source-2.6.20/arch/i386/kernel/acpi/boot.c 2007-04-12 10:15:46.000000000 -0700
+++ linux/arch/i386/kernel/acpi/boot.c 2007-04-22 10:21:34.000000000 -0700
@@ -600,24 +600,7 @@

EXPORT_SYMBOL(acpi_unregister_ioapic);

-static unsigned long __init
-acpi_scan_rsdp(unsigned long start, unsigned long length)
-{
- unsigned long offset = 0;
- unsigned long sig_len = sizeof("RSD PTR ") - 1;

- /*
- * Scan all 16-byte boundaries of the physical memory region for the
- * RSDP signature.
- */
- for (offset = 0; offset < length; offset += 16) {
- if (strncmp((char *)(phys_to_virt(start) + offset), "RSD PTR ", sig_len))
- continue;
- return (start + offset);
- }
-
- return 0;
-}

static int __init acpi_parse_sbf(unsigned long phys_addr, unsigned long size)
{
@@ -753,21 +736,11 @@

unsigned long __init acpi_find_rsdp(void)
{
+ struct acpi_pointer addr;
unsigned long rsdp_phys = 0;

- if (efi_enabled) {
- if (efi.acpi20 != EFI_INVALID_TABLE_ADDR)
- return efi.acpi20;
- else if (efi.acpi != EFI_INVALID_TABLE_ADDR)
- return efi.acpi;
- }
- /*
- * Scan memory looking for the RSDP signature. First search EBDA (low
- * memory) paragraphs and then search upper memory (E0000-FFFFF).
- */
- rsdp_phys = acpi_scan_rsdp(0, 0x400);
- if (!rsdp_phys)
- rsdp_phys = acpi_scan_rsdp(0xE0000, 0x20000);
+ if (!ACPI_FAILURE(acpi_find_root_pointer(ACPI_PHYSICAL_ADDRESSING,&addr)))
+ rsdp_phys=addr.pointer.physical;

return rsdp_phys;
}

diff -ur linux-2.6.20/arch/i386/mach-es7000/es7000plat.c linux/arch/i386/mach-es7000/es7000plat.c
--- linux-source-2.6.20/arch/i386/mach-es7000/es7000plat.c 2007-04-12 10:15:46.000000000 -0700
+++ linux/arch/i386/mach-es7000/es7000plat.c 2007-04-22 10:25:08.000000000 -0700
@@ -35,6 +35,7 @@
#include <linux/reboot.h>
#include <linux/init.h>
#include <linux/acpi.h>
+#include <linux/efi.h>
#include <asm/io.h>
#include <asm/nmi.h>
#include <asm/smp.h>
@@ -91,6 +92,52 @@
ioapic_renumber_irq = es7000_rename_gsi;
}

+
+ static unsigned long __init
+ es7000_acpi_scan_rsdp (
+ unsigned long start,
+ unsigned long length)
+ {
+ unsigned long offset = 0;
+ unsigned long sig_len = sizeof("RSD PTR ") - 1;
+
+ /*
+ * Scan all 16-byte boundaries of the physical memory region for the
+ * RSDP signature.
+ */
+ for (offset = 0; offset < length; offset += 16) {
+ if (strncmp((char *) (start + offset), "RSD PTR ", sig_len))
+ continue;
+ return (start + offset);
+ }
+
+ return 0;
+ }
+
+
+ unsigned long __init
+ es7000_acpi_find_rsdp (void)
+ {
+ unsigned long rsdp_phys = 0;
+
+ if (efi_enabled) {
+ if (efi.acpi20)
+ return __pa(efi.acpi20);
+ else if (efi.acpi)
+ return __pa(efi.acpi);
+ }
+ /*
+ * Scan memory looking for the RSDP signature. First search EBDA (low
+ * memory) paragraphs and then search upper memory (E0000-FFFFF).
+ */
+ rsdp_phys = es7000_acpi_scan_rsdp (0, 0x400);
+ if (!rsdp_phys)
+ rsdp_phys = es7000_acpi_scan_rsdp (0xE0000, 0xFFFFF);
+
+ return rsdp_phys;
+ }
+
+
/*
* Parse the OEM Table
*/
@@ -166,7 +213,8 @@
int i;
struct acpi_table_sdt sdt;

- rsdp_phys = acpi_find_rsdp();
+ /* FIXME -- can we use the general acpi_find_rsdp() ? */
+ rsdp_phys = es7000_acpi_find_rsdp();
rsdp = __va(rsdp_phys);
if (rsdp->rsdt_address) {
struct acpi_table_rsdt *mapped_rsdt = NULL;
```

---

### Post by redpoint7 on 2007-04-30
Hi, 

thx a lot for the reply, but the patching didn't work for me.
Therefor I changed the two source files on my own, now ACPI is working fine

By the way there is an error in the code:
+ if (!ACPI_FAILURE(acpi_find_root_pointer(ACPI_PHYSICA L_ADDRESSING,&addr)))

"ACPI_PHYSICA L_ADDRESSING" --> there should be no whitespace, so "ACPI_PHYSICAL_ADDRESSING"

bye

---

### Post by dkdk_it on 2007-05-02
Hello,
I've tried with kernel 2.6.21.1 and it returns an error:
```
patch: **** malformed patch at line 5: EXPORT_SYMBOL(acpi_unregister_ioapic);
```

Can you help me please?!?

---

### Post by redpoint7 on 2007-05-03
> **dkdk_it said:**
> Hello,
I've tried with kernel 2.6.21.1 and it returns an error:
```
patch: **** malformed patch at line 5: EXPORT_SYMBOL(acpi_unregister_ioapic);
```

Can you help me please?!?

I got the same error when I tried to use the patch on the 2.6.20 kernel, therefore I changed the two source files on my own. It is pretty simple:

@@ -600,24 +600,7 @@ --> means, 24 lines after the line 600 in the original file will be replaced to 7 lines in the new file. 
A minus in the beginning of a line means that this is the old code you have to remove and a plus means you have to add this code. 
In fact this is only a matter of copy and paste and you will be done in a few minutes. 

bye

---

### Post by PatheticMoFo on 2007-05-03
I'm going to have to try this later, I really want to get the battery monitor working on my C100 too and was frustrated that it didn't work when I installed it. Thanks a lot! 

By the way, Is anyone else here having trouble with their wireless card scanning for networks (on the same laptop)? For some reason mine says it can't scan, and the orinoco modules are loaded.

---

### Post by dkdk_it on 2007-05-03
I have not found this code in 2.6.21.1 source... can I leave out this?!?

```
@@ -166,7 +213,8 @@
int i;
struct acpi_table_sdt sdt;

- rsdp_phys = acpi_find_rsdp();
+ /* FIXME -- can we use the general acpi_find_rsdp() ? */
+ rsdp_phys = es7000_acpi_find_rsdp();
rsdp = __va(rsdp_phys);
if (rsdp->rsdt_address) {
struct acpi_table_rsdt *mapped_rsdt = NULL;
```

---

### Post by redpoint7 on 2007-05-04
there is no line "rsdp_phys = acpi_find_rsdp();" ?
In the 2.6.20 version I recognized that this part:
int i;
struct acpi_table_sdt sdt;

was in a different format (more spaces and tab-spaces), which doesn't change anything about the code.

you have at least find out where in the code the method acpi_find_rsdp() is called (because you removed this method previously) and replace it with the new method es7000_acpi_find_rsdp(). Otherwise you will get defently errors ...

---

### Post by dkdk_it on 2007-05-04
Work fine! with 2.6.28.1 kernel... I'm trying to recompile new 2.6.21... see you later!!! :popcorn:

---

### Post by dkdk_it on 2007-05-04
Nothing to do! :( 

I have attached es7000plat.c, can anyone help me to replace  this code:

```
@@ -166,7 +213,8 @@
int i;
struct acpi_table_sdt sdt;

- rsdp_phys = acpi_find_rsdp();
+ /* FIXME -- can we use the general acpi_find_rsdp() ? */
+ rsdp_phys = es7000_acpi_find_rsdp();
rsdp = __va(rsdp_phys);
if (rsdp->rsdt_address) {
struct acpi_table_rsdt *mapped_rsdt = NULL;
```

THANKS!

[COLOR="Red"]**EDIT: which kernel version you have used?**[/COLOR]

---

### Post by Paradoxdruid on 2007-05-04
Hello dkdk_it,

I looked at your uploaded code--  the acpi_table generation at the end seems quite different then in the kernel the patch was written for.

The source I used was obtained by ```
sudo aptitude install linux-source-2.6.20
```
Then I unpacked the source (in /usr/src), made a symbolic link from /usr/src/linux to /usr/src/linux-2.6.20 and patched against that.

Good luck with your efforts--  it took me a while, but now I really feel like my little old Acer C100 is doing fine! ...  if only I could get Gournal to actually save pages.

---

### Post by theory_prof on 2007-05-17
I have eagerly looked at all the patching going on here, since I have had to run my Acer Travelmate C100
without power management due to this "Checksum" error.:(

I have a hard time getting through all this lunux lingo in this thread. Can someone explain what is going on here?
So I have this patch, right, and then I have to "apply" it right , and then recompile? Is that correct?:confused:

If so, my kernel is 2.6.15-23-368, so does that mean I have to find another patch that someone wrote for
this specific kernel, or would the patch posted here work anyways?

I would really appreciate guidance...

---

### Post by redpoint7 on 2007-05-21
Hi,

to get ACPI to work for the C100 you need to make a few changes to the kernel source files. As I described it in a previous post, you just have to edit these two source files and you don't need to know any programming language to do this. "copy & past"-knowledge is enough ;-)
Then follow a simple "how-to"-guide to compile the kernel and it should work (if you get errors during compiling you probably made some mistakes during your changes in the source files).

I wasted lots of time with this patch, trying to get it working, without any success, so I advise to do the changes on your own.  

If it works on a 2.6.15 kernel I can't say, but you can try it with this kernel or upgrade to a current ubuntu version, where it works for sure.

---

### Post by theory_prof on 2007-06-05
Thanks, I am back from a conference on Discrete Math, so I will try to get this done now. 
I will report back.

---

### Post by dkdk_it on 2007-06-06
I think it doesn't work... I have tried with 2.6.20.15 kernel but nothing to do!
Lastest "patchable" kernel is 2.6.20.3.
Now, I would like to try new 2.6.20.16 kernel... I'll report results to you!

---

### Post by theory_prof on 2007-06-17
I downloaded the vanilla 2.6.20 kernel from kernel.org, and I got the same error
(Actually, this is for 2.6.20.3, but I also tried 2.6.20 and the only difference was
the error occured on line 5)

patching file arch/i386/kernel/acpi/boot.c
patch: **** malformed patch at line 6: EXPORT_SYMBOL(acpi_unregister_ioapic);

I am using  Dapper, so 
```
sudo aptitude install linux-source-2.6.20
```
gives
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-source-2.6.20"

It would help me to know:
How do get the code where tha pacth does not give errors?

> **Paradoxdruid said:**
> Hello dkdk_it,

I looked at your uploaded code--  the acpi_table generation at the end seems quite different then in the kernel the patch was written for.

The source I used was obtained by ```
sudo aptitude install linux-source-2.6.20
```
Then I unpacked the source (in /usr/src), made a symbolic link from /usr/src/linux to /usr/src/linux-2.6.20 and patched against that.

Good luck with your efforts--  it took me a while, but now I really feel like my little old Acer C100 is doing fine! ...  if only I could get Gournal to actually save pages.

---

### Post by theory_prof on 2007-06-17
[QUOTE=theory_prof;2864210]I downloaded the vanilla 2.6.20 kernel from kernel.org, and I got the same error
(Actually, this is for 2.6.20.3, but I also tried 2.6.20 and the only difference was
the error occured on line 5)

patching file arch/i386/kernel/acpi/boot.c
patch: **** malformed patch at line 6: EXPORT_SYMBOL(acpi_unregister_ioapic);

Plz ignore the part about not finding linux-source, I was able to get download the file
and get the same error for the patch command....

**Paradoxdruid, can you update the patch such there is no error, that would be like Christmas....**

---

### Post by theory_prof on 2007-06-17
> **dkdk_it said:**
> I think it doesn't work... I have tried with 2.6.20.15 kernel but nothing to do!
Lastest "patchable" kernel is 2.6.20.3.
Now, I would like to try new 2.6.20.16 kernel... I'll report results to you!

dkdk_it, can you email me the patched 2 files that worked for you and name the exact kernel.
Then I can just comiile that way...

---

### Post by theory_prof on 2007-06-19
Success! :KS

Earlier, Paradoxdruid posted a patch for the ACPI on the Acer Travelmate C 100. The patch worked
fine for me after recompiling the kernel.

But there is a problem: If the patch is copied from the webpage into a file and then one tries
to apply this patch file to the vanilla kernel code, there is an error message. I suspect the reason is that 
when the text of the patch is taken off the website in that process Tab characters get copied incorrectly.

Thus I edited the files boot.c  and  es7000plat.c by hand, as suggested earlier in another post.
I have attached the new files boot.c  and  es7000plat.c below. 

Then I recompiled the kernel (2.6.20) with those two files replaced. (Of course, compiling a kernel 
can have it's own hick-ups, but the reader will just have to tough this one out using all the documentation
on the net). 


Thanks to all that have posted, now I can take my Acer to Starbucks without worrying about power
all the time... :D

---

### Post by dkdk_it on 2007-06-29
> **theory_prof said:**
> dkdk_it, can you email me the patched 2 files that worked for you and name the exact kernel.
Then I can just comiile that way...

theory_prof excuse me but I had any issues with my DSL line... :( 

I'm happy for your NEW kernel!!! ;) Is it 2.6.20.3 version or 2.6.20???

---

### Post by theory_prof on 2007-07-12
It is 2.6.20.3. Does it make a difference?

Now, there is another issue. Under the new kernel auto-mount does not work properly,
and my PCI modem card does not work either. I think there is some problem with udev. 

My old kernel was 2.6.15-23 (the kernel from the Dapper CD) but in order to apply the patch I compiled the 2.6.20.3 kernel. I know that people who did a dist upgrade had these problems as well. Any ideas?

---

