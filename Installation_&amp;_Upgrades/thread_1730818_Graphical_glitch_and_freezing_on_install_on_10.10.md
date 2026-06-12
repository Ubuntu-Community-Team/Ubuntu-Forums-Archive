---
title: "Graphical glitch and freezing on install on 10.10"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by stomm on 2011-04-16
Hey everyone,

I've been having trouble trying to install ubuntu (and mint linux too) - I have the same problem with either version.

It's an Acer T180 tower PC, when I come to install it'll go through the motions of setting up the drive, copying files and then downloading/installing language packs. Randomly though between copying files and downloading/installing language packs it will just sit there and freeze. Sometimes it will just freeze and stay on the same image, other times it will freeze and what's best described as a window blinds effect will go across the whole screen. Either way the PC stops responding.

I've tried multiple downloads of iso files (ubuntu and then mint) - running on usb and also running from cd and dvd - same issue each time. I've made sure that the username is lowercase too (just in case).

The other thing I've tried is removing the separate nvidia graphics card and using just the internal one (again an nvidia card). Ubuntu will prompt that there are restricted drivers available - doesn't matter whether I install them or not - it still freezes just the same.

If anyone can make any suggestions or shed any light as to why this might be happening I'd appreciate it a lot!

Thanks in advance,

---

### Post by Dutch70 on 2011-04-17
Have you tried nomodeset & possibly other boot options? 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by stomm on 2011-04-21
Hi Dutch70,

I tried nomodeset, acpi=off, noapic, nolapic and acpi_osi="Linux" (even acpi_osi=\"Linux\") in the boot options (on their own and with different combinations) but I still have the same issue.

It's still freezing (9 times out of 10) on the point of downloading / installing the language packs. Whether it's on ubuntu or mint it still behaves the same. The screen will freeze and it will not go any further.

If you have any further suggestions I would really appreciate it. I'm at the point now of swapping ram sticks and changing the hard drive to see if that has any effect.

edit: I tried installing ubuntu using the alternate iso cd. I've installed it successfully but when I tried to update it froze again with the blinds effect.

I added acpi_osi=\"Linux\" to /etc/default/grub, updated grub and restarted. After an indeterminate amount of time (around when the update manager appeared froze again. I then added nomodeset to the /etc/default/grub (as well as acpi_osi=\"Linux\") - now it simply boots to the command line and goes no further.

---

### Post by Dutch70 on 2011-04-21
The only thing I would know is what I used to stop mine from freezing, It's post-#22 of the link in my sig. 
It worked for me on Ubuntu, Mint, Fedora, PCLinuxOS, basically anything that uses Compiz.

---

### Post by stomm on 2011-04-28
Hi Dutch70,

Again thank you for your patience with helping me out with this issue!

I've followed the instructions from [post 22]("http://ubuntuforums.org/showpost.php?p=8577751&postcount=22"), the machine froze again while removing the original packages. When I restarted I followed the prompt to repair it and after that ran the [COLOR="DarkSlateBlue"]sudo aptitude remove compiz compiz-core[/COLOR] command again. This time the machine flagged that everything was uninstalled so I carried on with the rest of the instructions.

The only issue I had after that was point four - [COLOR="DarkSlateBlue"]The compiz fusion icon should appear in your notification bar, there, right click -> Compiz options -> Indirect Rendering[/COLOR] - in my case Indirect Rendering was greyed out (not selectable).

I followed the other instructions anyway and I tried to reboot - frozen PC. Restarted again since and at the moment it's downloading updates and has been running for about ten minutes. Just in case I've got ubuntu 11.04 downloading as I type this.

I'll keep an eye on it now I've made the changes - hopefully that last freeze was because everything hadn't propagated properly yet. I'll keep you informed!

edit: internet connection went offline mid-update, it displayed that the connection was lost - I clicked OK to continue and I was faced with the flashing green window blinds again..... *weeps*

---

### Post by Dutch70 on 2011-04-28
I hate to hear that. I really don't know what else to suggest other than reporting it. That may also help lead you to an answer, as I'm sure it's been reported before. Seems like I remember reading about the "blinds" effect in some Ubuntu documentation before. 

This is just a guess. I don't want to lead you down the wrong path, but have you tried running memtest to check your memory? It needs to run at least 8 hours, overnight is better.

Also, does it freeze when you're running from the live cd or usb stick & have you checked the SMART data on your hdd with Disk Utility? 

Those 2 things would rule out your memory & hdd, but somehow I keep thinking it has to do with your graphics card. 
So many things can cause freezing problems. You may also want to try a different kernel.

---

### Post by stomm on 2011-07-19
Hi Dutch70,

Just to finally put this issue to bed - you were right it was the memory. Though a memory test found no issue originally - swapping it out with another ram stick has worked a treat.

Because the machine is 4 years old I struggled to find RAM of the same type (without buying new parts online and being charged a stupid amount) - now I've got some, tried a fresh install and it hasn't frozen at all.

So thank you for your help and advice, without it I wouldn't have a working machine now!

---

