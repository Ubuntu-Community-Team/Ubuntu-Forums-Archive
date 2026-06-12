---
title: "Ubuntu Installation Error"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Miguel_Mallari on 2015-01-16
[COLOR=#333333][FONT=UbuntuRegular]I tried Ubuntu 14.10 (64 & 32 Bit) & Ubuntu 12.10 (64 & 32 Bit) I get this error every time I select & entered "Install Ubuntu" *I am installing Ubuntu using a USB*[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.317787] Kernel panic - Not Syncing: VFS: Unable to mount root fs on unknown-block (2,0)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.317916] Pid: 1, comm: swapper/0 Not tainted 3.5.0 - 17 - generic #28 Ubuntu[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318033] Call Trace:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318150] [15bf0ec] panic + 0x81/0x17b[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318269] [c18aede1] mount_block_root + 0x19a/0x23d[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318387] [c115cb1d] ? sys_mlenod + 0x2d/0x30[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318503] [18aeff1] mount_root + 0x5e/0x64[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318615] [c18af145] prepare_namespace + 0x14e/0x192[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318731] [c114da05] ? sys_acces + 0x25/0x30[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318843] [c18ab75] kernel_init + 0x1b1/0x1b6[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.318956] [c18ae41c] ? . loglevel + 0x25/0x25[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.319068] [c18ae9c4] ? start_kernet + 0x363/0.363[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][21.319184] [c15d04fe] kernel_thread_helper + 0x6/0x10[/FONT][/COLOR]

---

### Post by TheFu on 2015-01-16
I can only guess that the USB creation process used failed or was corrupted somehow. I'd verify the ISO first and try creating the flash drive again. If that fails, I'd try a different flash drive - not all of them are compatible with all hardware.

If this is an ubuntu desktop, can you try running off the flash drive first? How does that work?

BTW - 12.10 isn't supported since last May.  You really need to use an LTS release if you can't reinstall every 6 months.  14.04 is the newest LTS release for a fresh install.  The next one is 16.04 ... in 1.5 yrs.

---

### Post by Miguel_Mallari on 2015-01-16
Uhh any other help?

---

### Post by QIII on 2015-01-16
Hello!

Did you try any of The Fu's suggestions?  If so, could you tell us what happened?

Please be aware that the Forums Staff recommends the use of currently supported releases of Ubuntu.  We would rather not have the volunteers here use their precious time dealing with issues in unsupported releases.  Please see [this]("http://ubuntuforums.org/showthread.php?t=2229730") for further information.

---

