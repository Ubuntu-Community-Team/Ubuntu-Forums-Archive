---
title: "Irfanview in WINE - Worked in Jaunty, not Karmic.  :("
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-06
Neither 4.23 nor 4.25 will run - they install fine, and yes, I did add MFC42.dll to the System 32 directory.

I know it's a Win program under WINE, but I thought I'd ask here first...

Here's the WINE text of the install of 4.23:

```

wine iview423_setup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x132b28 0x32f2bc) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:system:SystemParametersInfoW Unimplemented action: 88 (SPI_SETICONS)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
wine: Unhandled page fault on read access to 0x0420000c at address 0x685a4c46 (thread 0033), starting debugger...
Unhandled exception: page fault on read access to 0x0420000c in 32-bit code (0x685a4c46).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:685a4c46 ESP:0033e220 EBP:0033e268 EFLAGS:00010202(  R- --  I   - - - )
 EAX:04200004 EBX:685d9ff4 ECX:685e1fe4 EDX:00000000
 ESI:00000384 EDI:00000018
Stack dump:
0x0033e220:  00000384 00000000 0033e278 6857a503
0x0033e230:  0011d5c8 0000006c 00000000 00000000
0x0033e240:  00000000 00000000 683c295a 04200004
0x0033e250:  000004d0 00000090 00000000 683d5ff4
0x0033e260:  0015fa30 00000384 0033e308 68350197
0x0033e270:  00000384 00000018 0033e2d8 6834d21e
Backtrace:
=>0 0x685a4c46 GetObjectW+0x56() in gdi32 (0x0033e268)
  1 0x68350197 ImageList_AddMasked+0xa7() in comctl32 (0x0033e308)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
0x685a4c46 GetObjectW+0x56 in gdi32: movl	0x8(%eax),%eax
Modules:
Module	Address			Debug info	Name (77 modules)
PE	  400000-  542000	Export          i_view32
ELF	68000000-6801f000	Deferred        ld-linux.so.2
ELF	6801f000-6815c000	Deferred        libwine.so.1
ELF	6815c000-68176000	Deferred        libpthread.so.0
ELF	68176000-682ce000	Deferred        libc.so.6
ELF	682ce000-682d2000	Deferred        libdl.so.2
ELF	682d2000-682fa000	Deferred        libm.so.6
ELF	682fa000-68303000	Deferred        libnss_compat.so.2
ELF	68303000-6830e000	Deferred        libnss_nis.so.2
ELF	6830e000-6831b000	Deferred        libnss_files.so.2
ELF	6831b000-683ea000	Export          comctl32<elf>
  \-PE	68320000-683ea000	\               comctl32
ELF	683ea000-68547000	Deferred        user32<elf>
  \-PE	68400000-68547000	\               user32
ELF	68547000-685f3000	Export          gdi32<elf>
  \-PE	68560000-685f3000	\               gdi32
ELF	685f3000-686a8000	Deferred        comdlg32<elf>
  \-PE	68600000-686a8000	\               comdlg32
ELF	686a8000-68842000	Deferred        shell32<elf>
  \-PE	686c0000-68842000	\               shell32
ELF	68842000-688a5000	Deferred        shlwapi<elf>
  \-PE	68850000-688a5000	\               shlwapi
ELF	688a5000-688dd000	Deferred        winspool<elf>
  \-PE	688b0000-688dd000	\               winspool
ELF	688dd000-689ef000	Deferred        ole32<elf>
  \-PE	68900000-689ef000	\               ole32
ELF	689ef000-68a61000	Deferred        rpcrt4<elf>
  \-PE	68a00000-68a61000	\               rpcrt4
ELF	68a61000-68ae0000	Deferred        libfreetype.so.6
ELF	68ae0000-68af6000	Deferred        libz.so.1
ELF	68af6000-68b1d000	Deferred        libexpat.so.1
ELF	68b1d000-68bc2000	Deferred        winex11<elf>
  \-PE	68b30000-68bc2000	\               winex11
ELF	68bc2000-68bcb000	Deferred        libsm.so.6
ELF	68bcb000-68bd0000	Deferred        libuuid.so.1
ELF	68bd0000-68bee000	Deferred        libxcb.so.1
ELF	68bee000-68bf3000	Deferred        libxdmcp.so.6
ELF	68bf3000-68c15000	Deferred        imm32<elf>
  \-PE	68c00000-68c15000	\               imm32
ELF	68c15000-68c18000	Deferred        libxinerama.so.1
ELF	68c18000-68c1e000	Deferred        libxxf86vm.so.1
ELF	68c1e000-68c22000	Deferred        libxcomposite.so.1
ELF	68c22000-68c28000	Deferred        libxfixes.so.3
ELF	68c28000-68c33000	Deferred        libxcursor.so.1
ELF	68c33000-68c67000	Deferred        uxtheme<elf>
  \-PE	68c40000-68c67000	\               uxtheme
ELF	68c67000-68cb1000	Deferred        libcups.so.2
ELF	68cb1000-68cde000	Deferred        libgssapi_krb5.so.2
ELF	68cde000-68ceb000	Deferred        libavahi-common.so.3
ELF	68ceb000-68cfc000	Deferred        libavahi-client.so.3
ELF	68cfc000-68d27000	Deferred        libk5crypto.so.3
ELF	68d27000-68d30000	Deferred        libkrb5support.so.0
ELF	68d30000-68d34000	Deferred        libkeyutils.so.1
ELF	68d34000-68d4a000	Deferred        libresolv.so.2
ELF	68d4a000-68d5c000	Deferred        libtasn1.so.3
ELF	68d5c000-68dd8000	Deferred        libgcrypt.so.11
ELF	68dd8000-68e1a000	Deferred        libdbus-1.so.3
ELF	68e1a000-68e23000	Deferred        librt.so.1
ELF	69f04000-69f08000	Deferred        libcom_err.so.2
ELF	6a139000-6a143000	Deferred        libxrender.so.1
ELF	6b8c1000-6b973000	Deferred        libkrb5.so.3
ELF	6e27d000-6e286000	Deferred        libxrandr.so.2
ELF	6e2d5000-6e2f0000	Deferred        libice.so.6
ELF	6fd95000-6fec4000	Deferred        libx11.so.6
ELF	70195000-7023d000	Deferred        libgnutls.so.26
ELF	718f6000-718fa000	Deferred        libxau.so.6
ELF	751d2000-751e2000	Deferred        libxext.so.6
ELF	754c9000-754f6000	Deferred        libfontconfig.so.1
ELF	75eb8000-75ed1000	Deferred        libnsl.so.1
ELF	7625f000-762ba000	Deferred        advapi32<elf>
  \-PE	76270000-762ba000	\               advapi32
ELF	7906d000-79072000	Deferred        libgpg-error.so.0
ELF	7b800000-7b983000	Deferred        kernel32<elf>
  \-PE	7b820000-7b983000	\               kernel32
ELF	7bc00000-7bcba000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000e 
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	00000019    0
00000032 (D) C:\Program Files\IrfanView\i_view32.exe
	00000033    0 <==
Backtrace:
=>0 0x685a4c46 GetObjectW+0x56() in gdi32 (0x0033e268)
  1 0x68350197 ImageList_AddMasked+0xa7() in comctl32 (0x0033e308)
  2 0x00460997 in i_view32 (+0x60997) (0x00000378)
  3 0x00000000 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x685a4c46

```

It completes the install but I get a Windows-like dialog error box.  The icons also don't get their bitmaps, either.

---

### Post by ranch hand on 2009-10-07
Irfanview, now there is a name  I haven't come across for a while.  Used to run that under Win98.

---

### Post by Jerry N on 2009-10-07
I don't understand the choices in the poll.  IrFanView  and GIMP do not do the same thing at all. BTW, I had a lot better luck getting XnView to work under Wine.

---

### Post by emarkay on 2009-10-07
> **Jerry N said:**
> I don't understand the choices in the poll.  IrFanView  and GIMP do not do the same thing at all. BTW, I had a lot better luck getting XnView to work under Wine.

As an image manipulator (surely then GIMP is "overkill") they do.

Any other ideas?

Posted in Irfanview board:
[http://en.irfanview-forum.de/vb/showthread.php?t=5439](http://en.irfanview-forum.de/vb/showthread.php?t=5439)
and WINE:
[http://forum.winehq.org/viewtopic.php?p=32896#32896](http://forum.winehq.org/viewtopic.php?p=32896#32896)

---

### Post by jfernyhough on 2009-10-07
This doesn't answer your question, but 4.10 runs fine for me (obviously I haven't updated it in a while :) ).

--edit
Just tried the Zipped version (no install) and again it runs fine. I wonder if I have some extra .dll in my .wine//system32 directory...

My IView's toolbar buttons don't have icons either.

--edit2
Runs fine even if I rename the drive_c directory so there is no system32 for irfanview to find... weird... plus it gets the toolbar button icons back.

---

### Post by Jerry N on 2009-10-07
*As an image manipulator (surely then GIMP is "overkill") they do.*

As image manipulators, I consider IrFanView and XnView to be rather rudimentary and not at all in a class with GIMP or Photoshop.  However, their real strength is displaying thumbnails of an entire folder of images and being able to make changes in the entire group or in a selected subset of the group.  These changes include (but are not limited to )batch format conversions, batch rename, batch resize, and lossless crop and/or rotation of a group of .jpg files.  These functions are important (to me, at least) and I haven't found any Linux utility that does them as well as IrFanView and XnView.

---

### Post by Tibuda on 2009-10-07
I don't know what the poll have to do with the OP, but where is ImageMagick?

---

### Post by ranch hand on 2009-10-07
Where is gthumb, which is much more  comparable?

---

### Post by Seventh Reign on 2009-10-07
Irfanview was awesome a few years ago.  I'm more partial to Picasa or gwenview for quick viewing. Gimp for Editing.

---

### Post by emarkay on 2009-10-08
The poll was a secondary idea - and I have NOT studied in detail the alteranatives :)  I am just used to and like the Irfanview interface and editing abilities.

Now, on to the problem!  ;)

---

### Post by emarkay on 2009-10-08
D'oh! I forgot to read my old notes! It says real clearly: "Once installed, edit i_view32.ini and delete the lines following "[Toolbar]"at the bottom." 
 
Thanks!

---

### Post by Jesus_Valdez on 2009-10-08
> **Jerry N said:**
> *As an image manipulator (surely then GIMP is "overkill") they do.*

As image manipulators, I consider IrFanView and XnView to be rather rudimentary and not at all in a class with GIMP or Photoshop.  However, their real strength is displaying thumbnails of an entire folder of images and being able to make changes in the entire group or in a selected subset of the group.  These changes include (but are not limited to )batch format conversions, batch rename, batch resize, and lossless crop and/or rotation of a group of .jpg files.  These functions are important (to me, at least) and I haven't found any Linux utility that does them as well as IrFanView and XnView.
Nautilus does some of that fuctions the last time I checked.

You just need nautlius-image-converter and extras like that.

But nevermind, I'am glad that Irfanview works under wine for Karmic.

---

