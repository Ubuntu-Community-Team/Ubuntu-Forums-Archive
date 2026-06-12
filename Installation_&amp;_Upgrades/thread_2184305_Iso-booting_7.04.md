---
title: "Iso-booting 7.04"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by gnometorule on 2013-10-28
Following the instructions of the iso-booting thread at [http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847) (similar to the official grub2 wiki page), I receive a 'no kernel found' error message when I click my new menu entry in the grub 2 menu at boot time. I heard (when asking on stackoverflow), and believe read somewhere (don't remember source), that adding iso images to the grub2 menu for distros earlier than 9.xx is not possible. 

(1) Is that true? (2) If not, (a) should an adjustment to the above work, or (b) is there another method (not grml mentioned on the wiki page: i tried that first; entry added, but when clicking it I return, after my computer goes busy briefly, to the grub2 menu, with no error message)?

My distro is 12.04. I dual boot with Windows 7. My grub2 version is 1.99-21ubuntu3.1.

I should add what exactly I added at the end of my 40_custom file (iso image in <user>/Downloads folder of Linux, which is installed on sda6):

```

menuentry "Ubuntu 7.04" {
    set isofile="/home/<myname>/Downloads/ubuntu-7.04-desktop-i386.iso"
    loopback loop (hd0,6)$isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/casper/initrd.lz
}

```

I also tried not defining the isofile var, and instead typing out the name twice later; and this syntax:
```

menuentry "Ubuntu 7.04" {
    set isofile="/home/<myname>/Downloads/ubuntu-7.04-desktop-i386.iso"
    loopback loop (hd0,6)$isofile
    set root=(loop)
    linux /casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
    initrd /casper/initrd.lz
}

```

---

### Post by VMC on 2013-10-28
The only difference from my loop-back is i have '*set root='(hdX,X*)', just before the set isofile.
Are you sure about (hd0,6) location of the iso file. 
go to grub prompt type: ```
ls (hd0,6)[COLOR=#000000][FONT=Ubuntu Mono]/home/<myname>/Downloads/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] and see what it finds.[/FONT][/COLOR]

---

### Post by oldfred on 2013-10-28
I vaguely remember older versions could not be loop mounted. I still have not been able to loop mount server nor alternative versions. They have to be configured to work with loop mount.

Are internal names & paths correct. I often have to look in ISO to find paths, names, & boot options as they sometimes even change with Ubuntu.

I have not tried it except with Puppy, but you supposedly can extract kernel & init and then boot with those from outside ISO and then mount ISO (somehow).

---

### Post by gnometorule on 2013-10-28
Thanks for the feedback. I don't think that setting root to hd0,6 matters (sda6 is the right drive) - it should only affect how precisely to refer to the location of the iso image later.

I assume, with the second reply, that it is either a different path on the iso (have not confirned that); or, more likely, that the iso must be prepared in some way that older distros didn't do. It's probably impossible, but i keep this open a bit longer just in case some grub master happens to swing by.

---

