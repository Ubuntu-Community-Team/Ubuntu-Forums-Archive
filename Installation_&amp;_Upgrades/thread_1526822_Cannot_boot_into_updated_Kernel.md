---
title: "Cannot boot into updated Kernel"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by darkmakozu on 2010-07-08
Hello fellow Ubuntu users, I recently updated the kernel of lucid from 2.6.32-22 to the ""-23 release through update manager. Now whenever i try to boot the new kernel from GRUB the screen goes black and the computer stops responding with the caps lock and scroll lock lights flashing on the keyboard.

I can still boot into ""-22 fine and keep using ubuntu.

My first thought that the problem was the newer kernel itself so I tried to update to 2.6.33-5 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) but the same boot problem exists within this one also.

Because it goes straight into the black screen after GRUB I have no way of telling what has happened without error messages. Would this appear in any log files and if so which ones?

Any help would be thankfully appreciated.
~Makozu

---

### Post by ashleycrue123 on 2010-07-10
Hi,

I've had this problem with the last two kernel updates and I'm having to press shift key to go back to an earlier kernel. 

Any suggestions as to what the problem is and a possible solution would be a help.

I'm using the netbook remix on a Toshiba satellite A40-151.

Thanks

Ashley

---

### Post by ashleycrue123 on 2010-07-27
Sorry if this has been answered else where but there is no indication.

This problem still continues after the lastest update.:(

Has anyone else had this and did they find a solution?

---

### Post by davidmohammed on 2010-07-27
suggest - press e to edit your grub.

find the line with quiet splash

remove quiet splash and boot.

do you see any errors?

other boot options you can use 

nomodeset
noapic
nolapic

i.e.

add one or more of these BEFORE quiet splash

---

### Post by ashleycrue123 on 2010-07-29
> **davidmohammed said:**
> suggest - press e to edit your grub.

find the line with quiet splash

remove quiet splash and boot.

do you see any errors?

other boot options you can use 

nomodeset
noapic
nolapic

i.e.

add one or more of these BEFORE quiet splash

I removed the quiet splash line and got 

9c8
initrd /boot/initrd.img-2.6.32-24-generic

Thanks

---

### Post by ronparent on 2010-07-29
I believe david suggested moving only the words 'quied splash' from the line and then following the instructions to boot the shortened boot line.

---

### Post by ashleycrue123 on 2010-07-30
Thanks for pointing out the mistake.

I tried that and there is no error, says its all OK but I still get the same result.

However, when I switch of the laptop and then turn it back on again 'quiet splash' is there. Does it need to be completely deleted? if so, how do I do that?

---

### Post by davidmohammed on 2010-07-30
... so no error message was observed when you removed quiet splash - is this correct?

What happens if you add one of the other boot options?

---

### Post by ashleycrue123 on 2010-07-31
> **davidmohammed said:**
> ... so no error message was observed when you removed quiet splash - is this correct?

What happens if you add one of the other boot options?

That is correct.

In the original suggestion where you say about putting one of the original options in front of the quiet splash is that as in in front of those words or a new line before the one with quiet splash at the end? 

Sorry but I've never done this before.

---

### Post by davidmohammed on 2010-07-31
... actually before.

the line should look like


... <option> quiet splash --

e.g.

... nomodeset quiet splash --

---

### Post by ashleycrue123 on 2010-08-01
Thanks,

tied that and the others, none worked.

The laptop still does the same thing.....after the ubuntu splash screen nothing....

I did everything as you suggested, although because I haven't done this before I may have not done something although after adding the new instruction/command I'm sure I should have been saving/entering or something so that the new additions to the line stayed.

It did work with the new kernal in graphical recovery mode but when I rebooted it was back to square one....

I'm thinking of reinstalling but this is next to impossible due to broken CD/DVD drive.

---

### Post by davidmohammed on 2010-08-01
you mentioned you can boot to the desktop but in graphical recovery mode - that sounds like good news.

Please can you boot using graphical recovery mode.

Then use a terminal session and rename the following file

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

reboot

if this doesnt work - see if you can boot but with

nomodeset xforcevesa

---

### Post by ashleycrue123 on 2010-08-01
[QUOTE=davidmohammed;9665663]you mentioned you can boot to the desktop but in graphical recovery mode - that sounds like good news.

Please can you boot using graphical recovery mode.

Then use a terminal session and rename the following file

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup




I have tried this but keep getting the report 

 mv: cannot stat '/etc/x11/xorg.conf': no such file or directory

---

### Post by davidmohammed on 2010-08-01
the error message means that the file doesnt exist :(

Then I'm puzzled and out of ideas.

Yes you can reinstall from USB (see [here]("http://www.linuxconfig.org/install-ubuntu-lucid-lynx-linux-from-usb-stick")) -

but I'm sure there must be a simple answer.  

I think you said you can boot normally but you have to press shift on reboot to choose the old kernel - correct?

In that case,

sudo nano /etc/default/grub

change the grub_default value from 0 to the number corresponding to your kernel listed in grub - e.g. 0 is top, 2 is the second kernel, 4 is the third etc (assuming you have a recovery mode option immediately after each kernel).

save

sudo update-grub

You don't then need to press shift on reboot.

Lets hope that the next kernel update fixes your issue.

---

### Post by ashleycrue123 on 2010-08-02
I think you said you can boot normally but you have to press shift on reboot to choose the old kernel - correct?

In that case,

sudo nano /etc/default/grub

change the grub_default value from 0 to the number corresponding to your kernel listed in grub - e.g. 0 is top, 2 is the second kernel, 4 is the third etc (assuming you have a recovery mode option immediately after each kernel).

save

sudo update-grub

You don't then need to press shift on reboot.

Lets hope that the next kernel update fixes your issue.[/QUOTE]


Thankyou.

This worked.

---

### Post by FlashDude on 2010-08-07
I have the exact same problem with the same laptop I have tried about 6 different distro's with pretty much the same results.  I am not updating I am trying a new install.  After the splash screen if he looks quick I bet he will see some screwed up graphics right before the powered on black screen.

---

### Post by FlashDude on 2010-08-11
I am going to try these suggestions, It appears I am not the only one with this problem.  

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

