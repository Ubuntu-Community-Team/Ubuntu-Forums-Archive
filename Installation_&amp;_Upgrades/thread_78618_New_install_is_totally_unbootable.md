---
title: "New install is totally unbootable"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-10-18
Hiya guys,
I've just installed Ubuntu on my new machine, and I have a totally unbootable machine to the extent that repair mode doesn't boot either :(
This is the error that I get before the boot hangs, after 'Starting Hotplug Subsystem':
```
starting hotplug subsystem
snd-hda-intel can't be loaded
missing kernel or user mode driver snd-hda-intel
ignoring pci display device 01:05:0
8139too: already loaded
8139cp: already loaded
```
The boot process then hangs, and I can't get it to do anything.
Any help appreciated :)

Cheers

-Leezer-

---

### Post by mlomker on 2005-10-18
If you haven't done anything yet then I'd try reloading it a second time.  If that doesn't fix it then the fun begins.

Does the machine run Knoppix or the liveCD?

---

### Post by leezer3 on 2005-10-18
Knoppix (Live, 3.9 runs perfectly, but I have no Ubuntu livecd to hand)
Tried re-installing twice, once with full install and once with server- The same :(
Anyway, I'm ready for the fun!! :razz: 

Cheers

-Leezer-

---

### Post by mlomker on 2005-10-18
It looks like it's hanging on the sound card, so I'd start by going into the BIOS and disabling everything that can be disabled and still have the machine boot.  Unplug all your USB/Firewire devices...unplug any add-in cards that aren't required to boot, etc.

If it won't boot with everything unplugged/disabled then we might be out of luck.

---

### Post by leezer3 on 2005-10-18
Hiya once again,
Disabling sound from the BIOS has made the system bootable, but obviously I want sound :) (oh, and I'm suffering from the double-speed clock, but still)
I'm hoping that this will be a simple driver upgrade or kernel patch; This is my mobo:
[http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=693](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=693)
(Can't find it on the UK site)

Cheers

-Leezer

---

### Post by leezer3 on 2005-10-19
Bug filed:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18112](http://bugzilla.ubuntu.com/show_bug.cgi?id=18112)
Anyone else with the same issue or similar, please do add.

Cheers

-Leezer-

---

### Post by mlomker on 2005-10-19
> Anyone else with the same issue or similar, please do add.


Good job!  Hopefully they'll square the problem away for everyone.  Add-in sound cards are pretty cheap these days...if you have a couple bucks you could give that a shot.

---

### Post by XiX on 2005-10-19
Hi there,

I have the same prob! My first solution was to install the 5.04 version with a followed dist-upgrade! Since I had/have probs with the onboard ati express 200 I have not tested the sound yet :(

Im not really skilled in the desktop things I so I hope I'll find the help here :)

hopefully we'll find a solution since I would like to use this baby as media station and without sound ... mhh not realy niccce ;)

My hw config:
RS482M4-ILD ( [http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=693](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=693) )
[Onboard IEEE1394, 10/100 LAN, DVI connector]
1GB ram
AMD 3200+ Athlon 64
using the onboard graphic

---

### Post by pksings on 2005-10-19
Aww crap, I just put this on the wrong thread,..... please ignore......

Wow, I just went through this last night myself. 

Two IDE drives on IDE0, one SATA on whatever it is. I installed to the SATA. Grub installed itself on the master IDE as the IDE is the first driver per the BIOS.   My BIOS was set to boot from the SATA and of course would not.   I had to manually setup grub on the SATA (hd2,0).

If you manually setup grub then you know where it is. The installer automatically puts it on the first drive it finds. Which may or may not be the one you want to boot from.  It is also possible that your BIOS screws up booting, it you attempt to boot from the SATA and the BIOS is screwy the IDE is in the way. 

Make sure you have the latest BIOS for your motherboard installed. My MSI's had to be upgraded to work properly.

Hope this helps.

PK

---

### Post by Gorazd on 2005-10-19
[QUOTE=leezer3]Bug filed:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18112](http://bugzilla.ubuntu.com/show_bug.cgi?id=18112)
Anyone else with the same issue or similar, please do add.

Cheers

-Leezer-[/QUOTE]


I have the same problem....and am stuck :(

---

### Post by leezer3 on 2005-10-19
To XIX & Gorazad, please can you add confirmation of the bug to my Bugzilla post please? - The more people complain, the sooner it gets fixed :D

Cheers

-Leezer-

---

### Post by leezer3 on 2005-10-23
OK, we have a fix :D
First download the source for kernel version 2.6.13-4 or higher (That's what I used, won't guarantee that earlier versions work).
Now, apply the ALSA patch from here:
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0508.3/0083.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0508.3/0083.html)
Then make the kernel as per normal, and voila, sound should now be working.

Cheers

-Leezer-

---

### Post by XiX on 2005-10-26
Thanks for sharing your solution!

Could you please explain how to use this patch, since the link you posted is only an email which contians the code of the patch. Should I copy this code into a txt file and then how to apply/execute this patch?? sorry for the questions but Im a noob in these things.

TiA XiX

---

### Post by leezer3 on 2005-10-30
Hiya,
Sorry I was slightly late in getting back to you :rolleyes: 
Anyway, what I did was to copy this little lot into a text file, and save it into my home dir:
```
--- alsa-kernel/pci/hda/hda_intel.c 16 Aug 2005 13:29:57 -0000 1.17
+++ alsa-kernel/pci/hda/hda_intel.c 24 Aug 2005 13:09:36 -0000 1.21
@@ -72,7 +72,8 @@
"{ATI, SB450},"
"{VIA, VT8251},"
"{VIA, VT8237A},"
- "{SiS, SIS966}}");
+ "{SiS, SIS966},"
+ "{ULI, M5461}}");
MODULE_DESCRIPTION("Intel HDA driver");

#define SFX "hda-intel: "
@@ -142,9 +143,24 @@
*/

/* max number of SDs */
-#define MAX_ICH6_DEV 8
+/* ICH, ATI and VIA have 4 playback and 4 capture */
+#define ICH6_CAPTURE_INDEX 0
+#define ICH6_NUM_CAPTURE 4
+#define ICH6_PLAYBACK_INDEX 4
+#define ICH6_NUM_PLAYBACK 4
+
+/* ULI has 6 playback and 5 capture */
+#define ULI_CAPTURE_INDEX 0
+#define ULI_NUM_CAPTURE 5
+#define ULI_PLAYBACK_INDEX 5
+#define ULI_NUM_PLAYBACK 6
+
+/* this number is statically defined for simplicity */
+#define MAX_AZX_DEV 16
+
/* max number of fragments - we may use more if allocating more pages for BDL */
-#define AZX_MAX_FRAG (PAGE_SIZE / (MAX_ICH6_DEV * 16))
+#define BDL_SIZE PAGE_ALIGN(8192)
+#define AZX_MAX_FRAG (BDL_SIZE / (MAX_AZX_DEV * 16))
/* max buffer size - no h/w limit, you can increase as you like */
#define AZX_MAX_BUF_SIZE (1024*1024*1024)
/* max number of PCM devics per card */
@@ -201,7 +217,6 @@
};

/* Defines for ATI HD Audio support in SB450 south bridge */
-#define ATI_SB450_HDAUDIO_PCI_DEVICE_ID 0x437b
#define ATI_SB450_HDAUDIO_MISC_CNTR2_ADDR 0x42
#define ATI_SB450_HDAUDIO_ENABLE_SNOOP 0x02

@@ -259,6 +274,14 @@
snd_card_t *card;
struct pci_dev *pci;

+ /* chip type specific */
+ int driver_type;
+ int playback_streams;
+ int playback_index_offset;
+ int capture_streams;
+ int capture_index_offset;
+ int num_streams;
+
/* pci resources */
unsigned long addr;
void __iomem *remap_addr;
@@ -268,8 +291,8 @@
spinlock_t reg_lock;
struct semaphore open_mutex;

- /* streams */
- azx_dev_t azx_dev[MAX_ICH6_DEV];
+ /* streams (x num_streams) */
+ azx_dev_t *azx_dev;

/* PCM */
unsigned int pcm_devs;
@@ -293,6 +316,23 @@
unsigned int initialized: 1;
};

+/* driver types */
+enum {
+ AZX_DRIVER_ICH,
+ AZX_DRIVER_ATI,
+ AZX_DRIVER_VIA,
+ AZX_DRIVER_SIS,
+ AZX_DRIVER_ULI,
+};
+
+static char *driver_short_names[] __devinitdata = {
+ [AZX_DRIVER_ICH] = "HDA Intel",
+ [AZX_DRIVER_ATI] = "HDA ATI SB",
+ [AZX_DRIVER_VIA] = "HDA VIA VT82xx",
+ [AZX_DRIVER_SIS] = "HDA SIS966",
+ [AZX_DRIVER_ULI] = "HDA ULI M5461"
+};
+
/*
* macros for easy use
*/
@@ -361,6 +401,8 @@
azx_writel(chip, CORBLBASE, (u32)chip->corb.addr);
azx_writel(chip, CORBUBASE, upper_32bit(chip->corb.addr));

+ /* set the corb size to 256 entries (ULI requires explicitly) */
+ azx_writeb(chip, CORBSIZE, 0x02);
/* set the corb write pointer to 0 */
azx_writew(chip, CORBWP, 0);
/* reset the corb hw read pointer */
@@ -374,6 +416,8 @@
azx_writel(chip, RIRBLBASE, (u32)chip->rirb.addr);
azx_writel(chip, RIRBUBASE, upper_32bit(chip->rirb.addr));

+ /* set the rirb size to 256 entries (ULI requires explicitly) */
+ azx_writeb(chip, RIRBSIZE, 0x02);
/* reset the rirb hw write pointer */
azx_writew(chip, RIRBWP, ICH6_RBRWP_CLR);
/* set N=1, get RIRB response interrupt for new entry */
@@ -597,7 +641,7 @@
int i;

/* disable interrupts in stream descriptor */
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_sd_writeb(azx_dev, SD_CTL,
azx_sd_readb(azx_dev, SD_CTL) & ~SD_INT_MASK);
@@ -617,7 +661,7 @@
int i;

/* clear stream status */
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_sd_writeb(azx_dev, SD_STS, SD_INT_MASK);
}
@@ -687,8 +731,7 @@
}

/* For ATI SB450 azalia HD audio, we need to enable snoop */
- if (chip->pci->vendor == PCI_VENDOR_ID_ATI &&
- chip->pci->device == ATI_SB450_HDAUDIO_PCI_DEVICE_ID) {
+ if (chip->driver_type == AZX_DRIVER_ATI) {
pci_read_config_byte(chip->pci, ATI_SB450_HDAUDIO_MISC_CNTR2_ADDR,
&ati_misc_cntl2);
pci_write_config_byte(chip->pci, ATI_SB450_HDAUDIO_MISC_CNTR2_ADDR,
@@ -715,7 +758,7 @@
return IRQ_NONE;
}

- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev = &chip->azx_dev[i];
if (status & azx_dev->sd_int_sta_mask) {
azx_sd_writeb(azx_dev, SD_STS, SD_INT_MASK);
@@ -880,9 +923,15 @@
/* assign a stream for the PCM */
static inline azx_dev_t *azx_assign_device(azx_t *chip, int stream)
{
- int dev, i;
- dev = stream == SNDRV_PCM_STREAM_PLAYBACK ? 4 : 0;
- for (i = 0; i < 4; i++, dev++)
+ int dev, i, nums;
+ if (stream == SNDRV_PCM_STREAM_PLAYBACK) {
+ dev = chip->playback_index_offset;
+ nums = chip->playback_streams;
+ } else {
+ dev = chip->capture_index_offset;
+ nums = chip->capture_streams;
+ }
+ for (i = 0; i < nums; i++, dev++)
if (! chip->azx_dev[dev].opened) {
chip->azx_dev[dev].opened = 1;
return &chip->azx_dev[dev];
@@ -1190,7 +1239,7 @@
/* initialize each stream (aka device)
* assign the starting bdl address to each stream (device) and initialize
*/
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
unsigned int off = sizeof(u32) * (i * AZX_MAX_FRAG * 4);
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_dev->bdl = (u32 *)(chip->bdl.area + off);
@@ -1249,7 +1298,7 @@
if (chip->initialized) {
int i;

- for (i = 0; i < MAX_ICH6_DEV; i++)
+ for (i = 0; i < chip->num_streams; i++)
azx_stream_stop(chip, &chip->azx_dev[i]);

/* disable interrupts */
@@ -1265,10 +1314,10 @@

/* wait a little for interrupts to finish */
msleep(1);
-
- iounmap(chip->remap_addr);
}

+ if (chip->remap_addr)
+ iounmap(chip->remap_addr);
if (chip->irq >= 0)
free_irq(chip->irq, (void*)chip);

@@ -1280,6 +1329,7 @@
snd_dma_free_pages(&chip->posbuf);
pci_release_regions(chip->pci);
pci_disable_device(chip->pci);
+ kfree(chip->azx_dev);
kfree(chip);

return 0;
@@ -1294,7 +1344,8 @@
* constructor
*/
static int __devinit azx_create(snd_card_t *card, struct pci_dev *pci,
- int posfix, azx_t **rchip)
+ int posfix, int driver_type,
+ azx_t **rchip)
{
azx_t *chip;
int err = 0;
@@ -1320,9 +1371,20 @@
chip->card = card;
chip->pci = pci;
chip->irq = -1;
+ chip->driver_type = driver_type;

chip->position_fix = posfix;

+#if BITS_PER_LONG != 64
+ /* Fix up base address on ULI M5461 */
+ if (chip->driver_type == AZX_DRIVER_ULI) {
+ u16 tmp3;
+ pci_read_config_word(pci, 0x40, &tmp3);
+ pci_write_config_word(pci, 0x40, tmp3 | 0x10);
+ pci_write_config_dword(pci, PCI_BASE_ADDRESS_1, 0);
+ }
+#endif
+
if ((err = pci_request_regions(pci, "ICH HD audio")) < 0) {
kfree(chip);
pci_disable_device(pci);
@@ -1348,16 +1410,37 @@
pci_set_master(pci);
synchronize_irq(chip->irq);

+ switch (chip->driver_type) {
+ case AZX_DRIVER_ULI:
+ chip->playback_streams = ULI_NUM_PLAYBACK;
+ chip->capture_streams = ULI_NUM_CAPTURE;
+ chip->playback_index_offset = ULI_PLAYBACK_INDEX;
+ chip->capture_index_offset = ULI_CAPTURE_INDEX;
+ break;
+ default:
+ chip->playback_streams = ICH6_NUM_PLAYBACK;
+ chip->capture_streams = ICH6_NUM_CAPTURE;
+ chip->playback_index_offset = ICH6_PLAYBACK_INDEX;
+ chip->capture_index_offset = ICH6_CAPTURE_INDEX;
+ break;
+ }
+ chip->num_streams = chip->playback_streams + chip->capture_streams;
+ chip->azx_dev = kcalloc(chip->num_streams, sizeof(*chip->azx_dev), GFP_KERNEL);
+ if (! chip->azx_dev) {
+ snd_printk(KERN_ERR "cannot malloc azx_dev\n");
+ goto errout;
+ }
+
/* allocate memory for the BDL for each stream */
if ((err = snd_dma_alloc_pages(SNDRV_DMA_TYPE_DEV, snd_dma_pci_data(chip->pci),
- PAGE_SIZE, &chip->bdl)) < 0) {
+ BDL_SIZE, &chip->bdl)) < 0) {
snd_printk(KERN_ERR SFX "cannot allocate BDL\n");
goto errout;
}
if (chip->position_fix == POS_FIX_POSBUF) {
/* allocate memory for the position buffer */
if ((err = snd_dma_alloc_pages(SNDRV_DMA_TYPE_DEV, snd_dma_pci_data(chip->pci),
- MAX_ICH6_DEV * 8, &chip->posbuf)) < 0) {
+ chip->num_streams * 8, &chip->posbuf)) < 0) {
snd_printk(KERN_ERR SFX "cannot allocate posbuf\n");
goto errout;
}
@@ -1386,6 +1469,10 @@
goto errout;
}

+ strcpy(card->driver, "HDA-Intel");
+ strcpy(card->shortname, driver_short_names[chip->driver_type]);
+ sprintf(card->longname, "%s at 0x%lx irq %i", card->shortname, chip->addr, chip->irq);
+
*rchip = chip;
return 0;

@@ -1414,15 +1501,12 @@
return -ENOMEM;
}

- if ((err = azx_create(card, pci, position_fix[dev], &chip)) < 0) {
+ if ((err = azx_create(card, pci, position_fix[dev], pci_id->driver_data,
+ &chip)) < 0) {
snd_card_free(card);
return err;
}

- strcpy(card->driver, "HDA-Intel");
- strcpy(card->shortname, "HDA Intel");
- sprintf(card->longname, "%s at 0x%lx irq %i", card->shortname, chip->addr, chip->irq);
-
/* create codec instances */
if ((err = azx_codec_create(chip, model[dev])) < 0) {
snd_card_free(card);
@@ -1463,13 +1547,13 @@

/* PCI IDs */
static struct pci_device_id azx_ids[] = {
- { 0x8086, 0x2668, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ICH6 */
- { 0x8086, 0x27d8, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ICH7 */
- { 0x8086, 0x269a, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ESB2 */
- { 0x1002, 0x437b, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ATI SB450 */
- { 0x1106, 0x3288, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* VIA VT8251/VT8237A */
- { 0x1039, 0x7502, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* SIS966 */
- { 0x10b9, 0x5461, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ALI 5461? */
+ { 0x8086, 0x2668, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ICH6 */
+ { 0x8086, 0x27d8, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ICH7 */
+ { 0x8086, 0x269a, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ESB2 */
+ { 0x1002, 0x437b, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ATI }, /* ATI SB450 */
+ { 0x1106, 0x3288, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_VIA }, /* VIA VT8251/VT8237A */
+ { 0x1039, 0x7502, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_SIS }, /* SIS966 */
+ { 0x10b9, 0x5461, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ULI }, /* ULI M5461 */
{ 0, }
};
MODULE_DEVICE_TABLE(pci, azx_ids);
```

Next, you want to download & extract the current development release to your homedir. Then move the text file that you created into the root of the extracted folder.

Now, you want to open a terminal, and cd to the root of the extracted folder. There run:
```
patch -p1 < NAME_OF_PATCHFILE
```

Finally, build and install as per the alsa instructions.

Small final warning, unrelated to the patch- Anyone with one of these MSI motherboards SHOULD NOT upgrade to BIOS 1.1- This breaks ACPI under Linux, and it must be disabled from the BIOS before the machine boots, and quite typically Windoze refuses to boot without it :rolleyes: 

Cheers

-Leezer-

---

### Post by dookie on 2005-12-10
i've been having the same problems except with a clean install except i have to turn off my pci video to get things to boot right.  will the patch work for me to, or does that only fix the sound problem? anybody know if that patch doesn't work for me does anyone know where i could find one that would? thanks

---

### Post by Alessio on 2005-12-18
> **leezer3]Hiya,
Sorry I was slightly late in getting back to you :rolleyes: 
Anyway, what I did was to copy this little lot into a text file, and save it into my home dir:
```
--- alsa-kernel/pci/hda/hda_intel.c 16 Aug 2005 13:29:57 -0000 1.17
+++ alsa-kernel/pci/hda/hda_intel.c 24 Aug 2005 13:09:36 -0000 1.21
@@ -72,7 +72,8 @@
"{ATI, SB450},"
"{VIA, VT8251},"
"{VIA, VT8237A},"
- "{SiS, SIS966}}") said:**
> ;
+ /* streams (x num_streams) */
+ azx_dev_t *azx_dev;

/* PCM */
unsigned int pcm_devs;
@@ -293,6 +316,23 @@
unsigned int initialized: 1;
};

+/* driver types */
+enum {
+ AZX_DRIVER_ICH,
+ AZX_DRIVER_ATI,
+ AZX_DRIVER_VIA,
+ AZX_DRIVER_SIS,
+ AZX_DRIVER_ULI,
+};
+
+static char *driver_short_names[] __devinitdata = {
+ [AZX_DRIVER_ICH] = "HDA Intel",
+ [AZX_DRIVER_ATI] = "HDA ATI SB",
+ [AZX_DRIVER_VIA] = "HDA VIA VT82xx",
+ [AZX_DRIVER_SIS] = "HDA SIS966",
+ [AZX_DRIVER_ULI] = "HDA ULI M5461"
+};
+
/*
* macros for easy use
*/
@@ -361,6 +401,8 @@
azx_writel(chip, CORBLBASE, (u32)chip->corb.addr);
azx_writel(chip, CORBUBASE, upper_32bit(chip->corb.addr));

+ /* set the corb size to 256 entries (ULI requires explicitly) */
+ azx_writeb(chip, CORBSIZE, 0x02);
/* set the corb write pointer to 0 */
azx_writew(chip, CORBWP, 0);
/* reset the corb hw read pointer */
@@ -374,6 +416,8 @@
azx_writel(chip, RIRBLBASE, (u32)chip->rirb.addr);
azx_writel(chip, RIRBUBASE, upper_32bit(chip->rirb.addr));

+ /* set the rirb size to 256 entries (ULI requires explicitly) */
+ azx_writeb(chip, RIRBSIZE, 0x02);
/* reset the rirb hw write pointer */
azx_writew(chip, RIRBWP, ICH6_RBRWP_CLR);
/* set N=1, get RIRB response interrupt for new entry */
@@ -597,7 +641,7 @@
int i;

/* disable interrupts in stream descriptor */
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_sd_writeb(azx_dev, SD_CTL,
azx_sd_readb(azx_dev, SD_CTL) & ~SD_INT_MASK);
@@ -617,7 +661,7 @@
int i;

/* clear stream status */
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_sd_writeb(azx_dev, SD_STS, SD_INT_MASK);
}
@@ -687,8 +731,7 @@
}

/* For ATI SB450 azalia HD audio, we need to enable snoop */
- if (chip->pci->vendor == PCI_VENDOR_ID_ATI &&
- chip->pci->device == ATI_SB450_HDAUDIO_PCI_DEVICE_ID) {
+ if (chip->driver_type == AZX_DRIVER_ATI) {
pci_read_config_byte(chip->pci, ATI_SB450_HDAUDIO_MISC_CNTR2_ADDR,
&ati_misc_cntl2);
pci_write_config_byte(chip->pci, ATI_SB450_HDAUDIO_MISC_CNTR2_ADDR,
@@ -715,7 +758,7 @@
return IRQ_NONE;
}

- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
azx_dev = &chip->azx_dev[i];
if (status & azx_dev->sd_int_sta_mask) {
azx_sd_writeb(azx_dev, SD_STS, SD_INT_MASK);
@@ -880,9 +923,15 @@
/* assign a stream for the PCM */
static inline azx_dev_t *azx_assign_device(azx_t *chip, int stream)
{
- int dev, i;
- dev = stream == SNDRV_PCM_STREAM_PLAYBACK ? 4 : 0;
- for (i = 0; i < 4; i++, dev++)
+ int dev, i, nums;
+ if (stream == SNDRV_PCM_STREAM_PLAYBACK) {
+ dev = chip->playback_index_offset;
+ nums = chip->playback_streams;
+ } else {
+ dev = chip->capture_index_offset;
+ nums = chip->capture_streams;
+ }
+ for (i = 0; i < nums; i++, dev++)
if (! chip->azx_dev[dev].opened) {
chip->azx_dev[dev].opened = 1;
return &chip->azx_dev[dev];
@@ -1190,7 +1239,7 @@
/* initialize each stream (aka device)
* assign the starting bdl address to each stream (device) and initialize
*/
- for (i = 0; i < MAX_ICH6_DEV; i++) {
+ for (i = 0; i < chip->num_streams; i++) {
unsigned int off = sizeof(u32) * (i * AZX_MAX_FRAG * 4);
azx_dev_t *azx_dev = &chip->azx_dev[i];
azx_dev->bdl = (u32 *)(chip->bdl.area + off);
@@ -1249,7 +1298,7 @@
if (chip->initialized) {
int i;

- for (i = 0; i < MAX_ICH6_DEV; i++)
+ for (i = 0; i < chip->num_streams; i++)
azx_stream_stop(chip, &chip->azx_dev[i]);

/* disable interrupts */
@@ -1265,10 +1314,10 @@

/* wait a little for interrupts to finish */
msleep(1);
-
- iounmap(chip->remap_addr);
}

+ if (chip->remap_addr)
+ iounmap(chip->remap_addr);
if (chip->irq >= 0)
free_irq(chip->irq, (void*)chip);

@@ -1280,6 +1329,7 @@
snd_dma_free_pages(&chip->posbuf);
pci_release_regions(chip->pci);
pci_disable_device(chip->pci);
+ kfree(chip->azx_dev);
kfree(chip);

return 0;
@@ -1294,7 +1344,8 @@
* constructor
*/
static int __devinit azx_create(snd_card_t *card, struct pci_dev *pci,
- int posfix, azx_t **rchip)
+ int posfix, int driver_type,
+ azx_t **rchip)
{
azx_t *chip;
int err = 0;
@@ -1320,9 +1371,20 @@
chip->card = card;
chip->pci = pci;
chip->irq = -1;
+ chip->driver_type = driver_type;

chip->position_fix = posfix;

+#if BITS_PER_LONG != 64
+ /* Fix up base address on ULI M5461 */
+ if (chip->driver_type == AZX_DRIVER_ULI) {
+ u16 tmp3;
+ pci_read_config_word(pci, 0x40, &tmp3);
+ pci_write_config_word(pci, 0x40, tmp3 | 0x10);
+ pci_write_config_dword(pci, PCI_BASE_ADDRESS_1, 0);
+ }
+#endif
+
if ((err = pci_request_regions(pci, "ICH HD audio")) < 0) {
kfree(chip);
pci_disable_device(pci);
@@ -1348,16 +1410,37 @@
pci_set_master(pci);
synchronize_irq(chip->irq);

+ switch (chip->driver_type) {
+ case AZX_DRIVER_ULI:
+ chip->playback_streams = ULI_NUM_PLAYBACK;
+ chip->capture_streams = ULI_NUM_CAPTURE;
+ chip->playback_index_offset = ULI_PLAYBACK_INDEX;
+ chip->capture_index_offset = ULI_CAPTURE_INDEX;
+ break;
+ default:
+ chip->playback_streams = ICH6_NUM_PLAYBACK;
+ chip->capture_streams = ICH6_NUM_CAPTURE;
+ chip->playback_index_offset = ICH6_PLAYBACK_INDEX;
+ chip->capture_index_offset = ICH6_CAPTURE_INDEX;
+ break;
+ }
+ chip->num_streams = chip->playback_streams + chip->capture_streams;
+ chip->azx_dev = kcalloc(chip->num_streams, sizeof(*chip->azx_dev), GFP_KERNEL);
+ if (! chip->azx_dev) {
+ snd_printk(KERN_ERR "cannot malloc azx_dev\n");
+ goto errout;
+ }
+
/* allocate memory for the BDL for each stream */
if ((err = snd_dma_alloc_pages(SNDRV_DMA_TYPE_DEV, snd_dma_pci_data(chip->pci),
- PAGE_SIZE, &chip->bdl)) < 0) {
+ BDL_SIZE, &chip->bdl)) < 0) {
snd_printk(KERN_ERR SFX "cannot allocate BDL\n");
goto errout;
}
if (chip->position_fix == POS_FIX_POSBUF) {
/* allocate memory for the position buffer */
if ((err = snd_dma_alloc_pages(SNDRV_DMA_TYPE_DEV, snd_dma_pci_data(chip->pci),
- MAX_ICH6_DEV * 8, &chip->posbuf)) < 0) {
+ chip->num_streams * 8, &chip->posbuf)) < 0) {
snd_printk(KERN_ERR SFX "cannot allocate posbuf\n");
goto errout;
}
@@ -1386,6 +1469,10 @@
goto errout;
}

+ strcpy(card->driver, "HDA-Intel");
+ strcpy(card->shortname, driver_short_names[chip->driver_type]);
+ sprintf(card->longname, "%s at 0x%lx irq %i", card->shortname, chip->addr, chip->irq);
+
*rchip = chip;
return 0;

@@ -1414,15 +1501,12 @@
return -ENOMEM;
}

- if ((err = azx_create(card, pci, position_fix[dev], &chip)) < 0) {
+ if ((err = azx_create(card, pci, position_fix[dev], pci_id->driver_data,
+ &chip)) < 0) {
snd_card_free(card);
return err;
}

- strcpy(card->driver, "HDA-Intel");
- strcpy(card->shortname, "HDA Intel");
- sprintf(card->longname, "%s at 0x%lx irq %i", card->shortname, chip->addr, chip->irq);
-
/* create codec instances */
if ((err = azx_codec_create(chip, model[dev])) < 0) {
snd_card_free(card);
@@ -1463,13 +1547,13 @@

/* PCI IDs */
static struct pci_device_id azx_ids[] = {
- { 0x8086, 0x2668, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ICH6 */
- { 0x8086, 0x27d8, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ICH7 */
- { 0x8086, 0x269a, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ESB2 */
- { 0x1002, 0x437b, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ATI SB450 */
- { 0x1106, 0x3288, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* VIA VT8251/VT8237A */
- { 0x1039, 0x7502, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* SIS966 */
- { 0x10b9, 0x5461, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 }, /* ALI 5461? */
+ { 0x8086, 0x2668, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ICH6 */
+ { 0x8086, 0x27d8, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ICH7 */
+ { 0x8086, 0x269a, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ICH }, /* ESB2 */
+ { 0x1002, 0x437b, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ATI }, /* ATI SB450 */
+ { 0x1106, 0x3288, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_VIA }, /* VIA VT8251/VT8237A */
+ { 0x1039, 0x7502, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_SIS }, /* SIS966 */
+ { 0x10b9, 0x5461, PCI_ANY_ID, PCI_ANY_ID, 0, 0, AZX_DRIVER_ULI }, /* ULI M5461 */
{ 0, }
};
MODULE_DEVICE_TABLE(pci, azx_ids);
```

Next, you want to download & extract the current development release to your homedir. Then move the text file that you created into the root of the extracted folder.

Now, you want to open a terminal, and cd to the root of the extracted folder. There run:
```
patch -p1 < NAME_OF_PATCHFILE
```

Finally, build and install as per the alsa instructions.

Small final warning, unrelated to the patch- Anyone with one of these MSI motherboards SHOULD NOT upgrade to BIOS 1.1- This breaks ACPI under Linux, and it must be disabled from the BIOS before the machine boots, and quite typically Windoze refuses to boot without it :rolleyes: 

Cheers

-Leezer-


Can you help me?

root@kubuntu-laptop:/usr/src/linux-source-2.6.12# patch -p1 < patch_alsa
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- alsa-kernel/pci/hda/hda_intel.c 16 Aug 2005 13:29:57 -0000 1.17
|+++ alsa-kernel/pci/hda/hda_intel.c 24 Aug 2005 13:09:36 -0000 1.21
--------------------------
File to patch:

---

### Post by XiX on 2006-01-10
Hi leezer3,

I haven't solved this sound problem yet neither with breezy nor with the new dagger rls. I have compliled a new kernel 2.6.15 and installed the newest alsa version and applied the patch as you described.
Now I have the following questions regarding your solution:
Have you installed the 32 bit version or the 64 bit version, or doesn't this matter?
Is there any other thing I have to do after the installation of the patched alsa (e.g loading some modules or something else)?
Can you give me a hint what command/log/test or whatever I can check my installation
With what program could I test the functionality?

THX in advance

XiX

---

