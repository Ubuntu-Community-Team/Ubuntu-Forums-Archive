---
title: "Making bootable grub 2 CD in Lucid"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by moon_raker on 2010-05-03
It seems that the handy [COLOR="Navy"]grub-mkrescue --overlay=/boot/grub Grub2CD.iso [/COLOR]command that works nicely in Karmic is not the right way to create a cd iso in Lucid. Any ideas ?

~$ grub-mkrescue --overlay=/boot/grub Grub2CD.iso
[COLOR="Red"]Unrecognized option `--overlay=/boot/grub'[/COLOR]
Usage: /usr/bin/grub-mkrescue [OPTION] SOURCE...
Make GRUB rescue image.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --output=FILE           save output in FILE [required]

/usr/bin/grub-mkrescue generates a bootable rescue image with specified source files or directories.

Report bugs to <bug-grub@gnu.org>.

---

### Post by moon_raker on 2010-05-04
> **moon_raker said:**
> It seems that the handy [COLOR="Navy"]grub-mkrescue --overlay=/boot/grub Grub2CD.iso [/COLOR]command that works nicely in Karmic is not the right way to create a cd iso in Lucid. Any ideas ?

~$ grub-mkrescue --overlay=/boot/grub Grub2CD.iso
[COLOR="Red"]Unrecognized option `--overlay=/boot/grub'[/COLOR]
Usage: /usr/bin/grub-mkrescue [OPTION] SOURCE...
Make GRUB rescue image.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --output=FILE           save output in FILE [required]

/usr/bin/grub-mkrescue generates a bootable rescue image with specified source files or directories.

Report bugs to <bug-grub@gnu.org>.

I am keen to make a bootable grub CD for Lucid, so if anyone can help with the command required please .. ?

---

### Post by Herman on 2010-05-04
```
grub-mkrescue --output=rescue.iso /boot/grub
```I had a look at the new man page for grub-mkrescue, and you're right! 
It appears as though they have changed the command since last time I tried it. 
Thanks for posting.

I made up the above command, and tried it out and it seems to have worked for me. 
It created an .iso file in my /home/herman directory, and I burnt it to disc and booted it in another computer, (to make sure I can tell it's the CD that I'm booting and not my installed GRUB), and the CD booted to a command line.
After that I typed: configfile /grub.cfg  and I saw my own GRUB Menu, (from the computer I made the CD in). 
So it looks like that command works. 

Let me know if it works for you too. 

I think we can probably type any name we like for the .iso, it's not compulsory to name it 'rescue', that's just the name I made up.

For most of us, the  file path for our GRUB files that we want included in the .iso file will be /boot/grub. 
It's possible to type in a different file path. I imagine some people would use a different file path if they are making their own customized GRUB CD, and they would be working on that project in some other folder.

---

### Post by moon_raker on 2010-05-04
> **Herman said:**
> ```
grub-mkrescue --output=rescue.iso /boot/grub
```

I made up the above command, and tried it out and it seems to have worked for me. 
It created an .iso file in my /home/herman directory, and I burnt it to disc and booted it in another computer, (to make sure I can tell it's the CD that I'm booting and not my installed GRUB), and the CD booted to a command line.
After that I typed: configfile /grub.cfg  and I saw my own GRUB Menu, (from the computer I made the CD in). 
So it looks like that command works. 

Let me know if it works for you too. 


Herman, with your Grub experience and expertise I was hoping for you to spot my post. You are a star. The new command works perfectly and I feel secure. :D

---

### Post by Herman on 2010-05-04
:) Oh, good, thank you for the feedback, I must go and update my website.

You are a very good Ubuntu user to be making your own GRUB Rescue Disk. Everyone should make their own GRUB Rescue Disk, if everyone did, the world would be a better place. You're a star too. :KS

---

