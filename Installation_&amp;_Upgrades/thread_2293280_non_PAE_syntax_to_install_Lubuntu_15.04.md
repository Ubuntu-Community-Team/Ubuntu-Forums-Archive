---
title: "non PAE syntax to install Lubuntu 15.04"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by jim118 on 2015-09-03
Please move this post to correct forum if this is wrong. Not sure if I should use Virtualization, but my question seems more about the forcepae flag syntax rather than a virtualization situation. I'm stuck at step one; this may indeed turn into a copy files or virtualization issue if I can get past this step.

I'm trying to install Lubuntu 15.04 in Windows 7 Pro 32 bit as a VirtualBox virtual machine. 
[side note, just successfully installed 64 bit version on my AMD machine of 15.04]
I have mounted the iso file to a virtual CD.
I am getting the (now classic!) "no pae in CPU" at install, and I have gone through a number of posts on how to get around this.
But clearly I am not getting the syntax correct when I get to the prompt as the response I always get is "no such file or directory"
in the virtual CD I see the folder casper with the file initrd.lz in it.

Following directions, I can get to the prompt by 
1. Selecting install
2. Hitting F6 for advanced choices
3. hitting Esc gets me to the prompt named boot: 

Now on the first F6 page I see boot options along the bottom:
ed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash ---


I understand I need to add "forcepae -- forcepae" at the end of the command line.
BUT WHAT is the correct command?
I have tried the entire line as above:
ed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash ---   [but this seems like a choice of two commands...?]
as well as:
ed boot=casper
initrd=/casper/initrd.lz
and:
casper/initrd.lz
 and adding forcepae -- forcepae at the end.
have tried forcepae (etc.) by itself

I have put the command "install" before the lines.

I don't get why the return response is "no such file or directory"  !!!

Would someone give me the precise command line please?  No dot-dot-dot please! Assume I know utterly nothing!!

the image posted at [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) shows the forcepae -- forcepae somehow added to the suggested line!! It's not on 15.04. Am I supposed to edit something to make this appear? 

thanks

---

### Post by grahammechanical on 2015-09-03
Have you seen this?

[https://help.ubuntu.com/community/BootOptions/before--after](https://help.ubuntu.com/community/BootOptions/before--after)

It seems you may need to write forcepae twice. The same point is made here also.

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

Regards.

---

### Post by sudodus on 2015-09-04
**1. In BIOS mode:**

*In Ubuntu:*

During booting, when you see two small icons at the bottom of the screen, press any key (for example the Enter key), and you will get to the syslinux menu. At that menu you can select F6 etc according to the instructions in [this link](https://help.ubuntu.com/community/BootOptions) or the links posted by grahammechanical in the previous post.

*In Lubuntu:*

You get to a language selector, and after that to the syslinux menu.

**2. In UEFI mode:**

You get to a grub menu, which is very different from a syslinux menu.

---

### Post by sudodus on 2015-09-04
Do not remove anything. Add the [COLOR="#0000FF"]blue[/COLOR] text, and there should be a space character separating them from the previous boot option and from the hyphens ---

```
file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash [COLOR="#0000FF"]forcepae[/COLOR] --- [COLOR="#0000FF"]forcepae[/COLOR]
```

You can see the whole command line, if you use the following keys

Home
End
Left arrow
Right arrow

---

### Post by sudodus on 2015-09-04
If your computer has PAE, it is possible to toggle the settings in VirtualBox to emulate PAE or not in the virtual machine. If you can run 64-bit Lubuntu, the computer has PAE. Or are we talking about two different computers, one where you run 64-bit Lubuntu and one where you run Windows and VirtualBox and try to install Lubuntu 32-bit inside VirtualBox?

---

### Post by jim118 on 2015-09-04
Wow, the support here is EXCELLENT! You people rock!
Yes, I have two computers, one 64 bit and that was no problem. It was the 32 bit OS (altho Windoz says it is 64 bit ready)

I did write forcepae twice, also once, also with no spaces "forcepae--forcepae" as one post said...
But I did not have the full command line as pointed out. I could not see it all and didn't know to scroll left right. I've been using command lines in DOS and Amiga DOS since late 80's ! Just shows how the little unknowns can trip you up.

Easiest method was to force pae in Virtual Box. There was a tab and check box for that, and Voila! The 32 bit image is now installing.

[yes I still emulate Amiga too when nostalgic!]

I always keep an up-to-date Ubuntu boot disk. Saved me when hard drive crashed. Windoze "recovery" couldn't seem to load the CD driver, but Ubuntu could! How lame is that?

Still, new friends, I have SO MANY Windoze programs loaded I despair of ever moving easily to another platform... sigh. Known and comfortable old stuff. But I am strongly encouraged to use a VM when cruising unsafe sites. 

Thanks, awesome guys.

---

### Post by sudodus on 2015-09-04
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other users, who have similar problems :-)

---

