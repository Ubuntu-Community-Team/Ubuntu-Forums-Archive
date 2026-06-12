---
title: "Very, very simple question?"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by wontstoptalking on 2008-03-27
Just read this:
>  Re: Blinking Underscore in Top Left of Screen, Can't install!
Originally Posted by wontstoptalking
My friend's computer is a HP Pavilion A440, and I can NOT get Ubuntu (any distro) to install on it! After booting up the LiveCD, and hitting "start or install ubuntu" (or whatever the first one is) it boots up the kernel, then flashes an error "no DMI BIOS year, acpi=force is required to enable ACPI" and then shows the normal orange bar gliding left and right. After that orange bar glides left to right and back again for about 7 minutes, it just shows that flashing underscore in the top left corner, and I can't do anything about it. It just hangs. I have tried entering "acpi=force" into the F6 options in the LiveCD boot menu, and it did absolutely nothing. Then someone suggested that I add "acpi=off", and that got rid of the error, but it still went to the flashing underscore. This happens on all the distros I have tried.

Please help me! Please!
> Hi. I'm guessing your machine is like this one, which means you probably have an Intel graphics card built into the motherboard.

[http://h10025.www1.hp.com/ewfrf/wc/d...ct=391927&dlc=](http://h10025.www1.hp.com/ewfrf/wc/d...ct=391927&dlc=)

Usually that blinking underscore means there's a problem between the video hardware you have in your machine and the driver Ubuntu picked to run it. Ubuntu sometimes picks the wrong one, and that underscore is all that's left.

The easy way to fix that is, probably, to restart the machine. When you see the words "Grub ..." at the top, hit the escape key. You should get a menu of startup options.

Pick recovery mode, and when it reaches the prompt, try this:
Code:

nano -w /etc/X11/xorg.conf

Look for a line that starts with the word "Driver"; it will probably have a video driver listed after it. Change it to read "vesa" (in quotes), then press CTRL+O to save the file. Press CTRL+X to exit the editor, then enter the "reboot" command.

Now boot normally. Hopefully you should get some sort of working video, and that's a start. The acpi options are for power management; it sounds like your BIOS doesn't allow the kernel to manage power that way. Don't worry about that. It's probably not related to the video issue.

If these instructions don't work, your best bet is to start a thread in the Multimedia and Video or Absolute Beginner Talk sections. I'm sure someone will have a similar machine with similar issues, and can help you work through it.

Good luck!
K.Mandla

But I can't get past the first step: When does GRUB pop up for me to hit the Escape button to get to the settings?

Same thing every time. None of the options work, and nothing installs. In any distro, or in the alternate installer. I just need to be able to do what this guy says: Hit Escape when Grup pops up and I can fix my problem. But when it says "loading grub 1.5" and I hit ESC, nothing happens. It just takes me to the screen I talked about below this.

---

### Post by wontstoptalking on 2008-03-27
Anyone?

---

### Post by Islington on 2008-03-27
grub is popping up before the screen that lets you pick your OS.

---

### Post by wontstoptalking on 2008-03-27
I don't get that screen! I get a blue screen with white font that says "GNU GRUB version 0.97 (638K lower / 60352K upper memory" and below that:

"Linux (on /dev/hda1
Install GRUB to floppy disk (on /dev/fd0)
Install GRUB to Linux Partition (on /dev/hda1)
-   For help press 'c', then type: 'help'"

That's what it says. And I have already "installed GRUB to Linux partition many times, but I don't have any Linux distro installed because of the ERROR I'M GETTING! Does anyone understand me?

---

### Post by wontstoptalking on 2008-03-27
Help

---

### Post by munkyeetr on 2008-03-27
> **wontstoptalking said:**
> Help

Just be patient and someone who can help you will come along.

---

### Post by wontstoptalking on 2008-03-27
> 
Quote:
Originally Posted by wontstoptalking View Post
Help
Just be patient and someone who can help you will come along.
But not you?

---

### Post by wontstoptalking on 2008-03-27
Again, help.

---

### Post by wontstoptalking on 2008-03-27
I need help. Right now.

---

### Post by Islington on 2008-03-27
hmm, if you really need help try hitting up the irc channel. there are always people on that can help.

Okay I read the reply you posted.

when you pop in the live cd, what happens when you try some other options?

---

### Post by wontstoptalking on 2008-03-27
Same thing every time. None of the options work, and nothing installs. In any distro, or in the alternate installer. I just need to be able to do what this guy says: Hit Escape when Grup pops up and I can fix my problem. But when it says "loading grub 1.5" and I hit ESC, nothing happens. It just takes me to the screen I talked about above.

---

### Post by gunksta on 2008-03-27
What graphics card is in your computer? It may be possible to turn off ACPI and force it to use a lower level of graphics.

---

