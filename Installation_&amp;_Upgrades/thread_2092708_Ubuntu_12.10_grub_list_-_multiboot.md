---
title: "Ubuntu 12.10 grub list - multiboot"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2012-12-08
I have a number of machines with only Ubuntu installed, however, I usually want an Ubuntu multiboot - two or three versions, on each machine. Including perhaps a variant, such as Lubuntu.
Having installed Ubuntu 12.10, I notice that the Grub boot list is pretty lean. With Ubuntu 12.04, it was still possible to identify the partition name (sda6 etc) which made it possible to identify each installation.
But with 12.10 the partition name does not appear in the grub list. For example Lubuntu is shown as 12.04.1 (with no sda6)
Any suggestions please about how I can arrange to see a bit more information in the grub list?
tia

---

### Post by oldfred on 2012-12-08
I do it manually by turning off the os-prober and adding my own entries to 40_custom. But most will suggest Gub-Customizer as it is a gui.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

    
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by candtalan on 2012-12-08
Thank you for the reply. I am dismayed at the options. I could cope ok in the past with being told 'sda6' whatever, but my skill level is the advanced end of 'beginner'. Grub-customizer looks promising but PPA's are getting a bit out of my depth, hopefully an app will appear before too long.

I can pretty well cope ok with carefully just editing files so my preferred minimum information would be specific info to change 
'Ubuntu 12.04.1 LTS (12.04)'
to read
'Ubuntu 12.04.1 LTS (12.04)(sda6)'
(or anything to differentiate it from the other 12.04 entries...)

The actions to do this are somewhat buried amongst many other options in a number of very worthy grub 2 help pages, and written by people who can take a lot for granted in the instructions.

After my initial panic subsided I did notice that the new grub menu is a two stage list. The initial confusing one - with multiple identical entries(!) - includes
'Advanced options for Ubuntu 12.04.1 LTS (12.04)'
and when *this* is accepted, I THEN see references to (sda6) whatever. This will have to do for now, I do not really have the time to improve my expertise just yet.

There are good reasons why non expert Ubuntu users might want to run more than one Ubuntu install, multiboot, and I do hope that this situation will attract more elegant facilities. Although in the recent few years, things seem to have got worse not better. :-(
Again thanks for your reply.

---

### Post by darkod on 2012-12-08
It's not difficult, but that depends on how used you are...

First open the 40_custom file as oldfred mentioned:
gksu gedit /etc/grub.d/40_custom

Then open the grub.cfg with:
gksu gedit /boot/grub/grub.cfg

In the grub.cfg look in the section named 30_os-prober, it's towards the end of the file. All additional OSs discovered will be listed there, like:
menuentry Ubuntu XXXX {
lines of commands
}

Simply select and copy all of the entry, until the end } and paste it into the 40_custom. After you paste it, change the name to something like Ubuntu XXXX on sda6. Leave the commands between the {} as they are, only change the title to something that makes sense to you.

When you are done, save and close the file. Close the grub.cfg too. To recreate new grub.cfg run:
sudo update-grub

Now, first time the list will be quite long, since it will include the OSs that were located automatically, and the ones you created manually in 40_custom (they should be at the end of the list). After you have tested them all, boot the main OS (the one controlling grub), and disable the os-prober with:
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

After that you should see a smaller list with only your manual entries.

I forgot to mention, all above operations are done from the main OS that controls the grub. You have to be careful about that, otherwise the changes you make will not be reflected in the grub boot menu.

---

### Post by candtalan on 2012-12-10
Thanks

---

