---
title: "Computer Crashed, does not boot hd"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by IReadTheManual on 2011-08-26
Hello, I am writing this from a LiveDVD of 11.04. My machine, which is an Inspiron1501 with AMD64 dualcore crashed while running a working copy of 10.04LTS 32bit. At first Harddrived seemed unrecoverable, but not that may not be the case if I can mount it. HD is partitioned as 

[LIST=1]
[*]1 FAT which holds the OEM installer
[*]1 NTFS with a sub/ virtual NTFS (not as a file, but as a "partition", only readable from WinXX)
[*]1 Linux Swap
[*]1 Linux Extention 3 (I believe it is 3, as in EXT FS 3)
[/LIST]
Machine initially displayed: 
```

[       2.736258] Console: switching to colour frame buffer device 160x50
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```After following some advice, I booted into Win and shutdown cleanly. Which has made the machine only say this on boot:
```

No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```Now, to make things a little more complicated, my home directory is encrypted. Could I just copy that over to a new install provided I can get it to mount?


I would like to salvage this install if possible. Anyone ever dealt with this before?

Thanks!!

PS. I am a power user, I think. Feel free to say non-gui solutions if you know them

---

### Post by Hakunka-Matata on 2011-08-26
Can you download, run and post the output of boot_info_script please.
>  from forum member oldfred:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file  and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New  Reply Edit toolbar and then paste the contents between the generated [  code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible.  New Version is a zip file that you have to extract to get .sh to run.Here's a link to howto mount and copy encrypted /home folder: [http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

---

### Post by IReadTheManual on 2011-08-28
Works. :popcorn:


boot_info_script is very interesting. Thanks for the heads up.

Ok. Imaged entire HD, and key partitions. Ran into some problems with the encrypted home directory. Then it didn't mount right. Dropped in a new kernel, MBR, xserver setup, and fixed the file system errors. Ran differences against home directory copies, and figured out where problems were. Minimal Data Loss.

My ram seems fine, however my Harddrive may be having interesting IO errors. For the moment, linux can just skip those sectors since I need to pay for college more than a new laptop.


A working machine makes me very happy.
:guitar::guitar::guitar::guitar::guitar:

PS. I would mark this as fixed, but I want to just wait a day or two in case.

---

### Post by Hakunka-Matata on 2011-08-28
I'm glad you got it going.  Sounds like you did quite a lot of work cleaning up - straightening out.  Yes, boot_info_script is quite the tool, I agree.

---

