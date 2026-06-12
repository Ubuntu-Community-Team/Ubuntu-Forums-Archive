---
title: "fine dual boot,but windows causing probs :S"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Deicider on 2009-11-13
just installed karmic and xp.
Worked good,until i started installing applications in windows.
Adobe flash,drivers and other simple installations wont work,dunno,maybe cause at some point when installing the Installer there was a prob and rebooted or smth...and now its stuck,tried upgrades etc and download installer 4.5 which can't be installed :S 
While Dual booting works i think i must have to reinstall windows to fix this...how do i do this without hurting grub/linux?
Well this is not quite linux problem but still i dont wanna cause problems to linux.

---

### Post by darkod on 2009-11-13
I'm not sure you can install xp without it writing itself on the MBR. While you can select grub not to be installed when installing linux, MS doesn't give you options, I think. :)

But restoring grub should be easy.

---

### Post by Deicider on 2009-11-13
i'v tried in my previous installations to reinstall manualy grub;din;t worked.
Can you tell how do i restore grub?

---

### Post by darkod on 2009-11-13
Boot with Ubuntu CD but select advanced options and just grub prompt. Sorry don't know which number in the menu it is. Looks like:
grub>
Then it should be as simple as executing
install-grub (hd0)
update-grub2

The second command will usually find all your OS (ubuntu and xp) and make the grub menu automatically.

PS. All of this after you are done reinstalling xp.

---

### Post by presence1960 on 2009-11-13
> **Deicider said:**
> i'v tried in my previous installations to reinstall manualy grub;din;t worked.
Can you tell how do i restore grub?

after you reinstall windows you can restore GRUB.

For 9.04 and prior releases do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

For 9.10 see [here]("https://help.ubuntu.com/community/Grub2"). On right side of that page there is a menu with links. look for # 11-Reinstalling GRUB 2 and select #1-reinstalling from a Live CD. Follow those instructions

---

### Post by Deicider on 2009-11-13
Ok,installed windows,fixed.
But as the whole world knew,grub vanished.
i have karmic.
When using live cd i must enter the live mode right?(cause in the menu did not find anything that has to do with grub)
Am in right now.
Read the Grub 2 tut.
It says only that its default with karmic and how to upgrade,not how to in/reinstall.
I suppose i download with
$ sudo apt-get install grub2

after that,what do i do?

---

### Post by darkod on 2009-11-13
The link presence supplied in the bottom of the post, "for 9.10 see here". The explanation is not complex.

---

### Post by Deicider on 2009-11-13
saw it before,not complex but it doesnt show how to install,only how to upgrade.

---

### Post by Deicider on 2009-11-13
find it,its in the bottom,after the Themes...i thought that beyond that it was about looks,style ,etc...anyway,am gonna check it.

---

### Post by Deicider on 2009-11-13
can't do it,i think i'll have to reinstall ubuntu again :S

---

