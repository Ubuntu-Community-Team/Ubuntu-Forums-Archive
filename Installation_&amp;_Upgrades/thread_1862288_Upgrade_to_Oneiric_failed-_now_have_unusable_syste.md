---
title: "Upgrade to Oneiric failed- now have unusable system"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by sumithar on 2011-10-16
Please help- am stuck with an unusable system right now.

I was running Natty. I chose the in-place upgrade to Oneiric. I left it unattended and then when I came back later it had a blank screen and keyboard unresponsive. Tried switching off and on again- Grub came up, chose the kernel 3.0something option at the top- it gave me a blank screen.
Rebooted, Chose earlier kernel which I thought might be corresponding to natty- that didn't work either
So booted from CD with Natty and tried to install Natty all over again. Got a message that installer crashed and asked me to attach these 2 files /var/log/syslog and /var/log/partman

I posted a bug on launchpad.

But in the meantime I don't have a system I can really work with- I'm booting off CD right now.

What can I do?

When I try to install from LiveCd it gives these options- see AllocateDrivespace.png attached.
If I choose the 4th option it gives this additional screen(AllocateDrivespace2.png)- 
not sure how to proceed at that point.  Can I be sure that a clean install will only  use that 10GB partition?
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485760   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda3            1306        9328    64435200   83  Linux
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
```

The sda3 is where I have my user directory with all my videos and documents and other goodies.

Can I wipe out sda1 and install Natty there fresh?  Would that work.

As I said, please help- I really don't want to format the whole harddrive- even having to reinstall the OS is a serious PITA I could have done w/o, but I obviously don't learn since my inplace upgrade from meerkat to natty had similar issues and I did end up wiping the HDD and installing natty from a downloaded CD!

---

### Post by 23dornot23d on 2011-10-16
You should back up any data you need onto a separate drive before proceeding.

---

### Post by sumithar on 2011-10-16
Are you saying that just to be on the safe side or will I have no choice to back up and restore things?  I was hoping that the partitioning schem I had chosen would insulate my user directory from the os.

Anyway, I started to do that...See attached screenshot-  I want to just back up this entire folder.  I wonder if those entries which are x'ed out can also be included somehow in the copy?  It currently won't let me.

---

### Post by eastwood_systems on 2011-10-16
I have nearly the same situation.  The upgrade was in the fetching packages stage when I left it.  Came back to a blank screen, unresponsive to keyboard.  After power-cycling, it boots partially: I get the Ubuntu logo with the 5 dots underneath, then it goes to a text screen with various messages, the last one being "* Checking battery state   [OK]", then it just hangs.  Keystrokes are echoed, but it doesn't react to any commands other than ctrl-alt-del.

Booting to the older kernal listed in the grub menu gives similar results.  I can boot to recovery mode and get a command prompt, but don't know what to do from there.

I have Oneiric on a bootable flash drive, but would like to avoid a complete re-install.

I am running a Dell system with a Pentium 4 processor and the on-board Intel Express display adapter.

---

### Post by sumithar on 2011-10-16
> **eastwood_systems said:**
> I have nearly the same situation.  The upgrade was in the fetching packages stage when I left it.  Came back to a blank screen, unresponsive to keyboard.  After power-cycling, it boots partially: I get the Ubuntu logo with the 5 dots underneath, then it goes to a text screen with various messages, the last one being "* Checking battery state   [OK]", then it just hangs.  Keystrokes are echoed, but it doesn't react to any commands other than ctrl-alt-del.

Booting to the older kernal listed in the grub menu gives similar results.  I can boot to recovery mode and get a command prompt, but don't know what to do from there.

I have Oneiric on a bootable flash drive, but would like to avoid a complete re-install.

I am running a Dell system with a Pentium 4 processor and the on-board Intel Express display adapter.

The specifics you've detailed are what I'm facing too like the screen with the dots and the battery message.  Like you I'm booting off an external device currently (Natty off a CD) 

I too want to avoid a complete reinstall, I had installed a handful of programs and utilities plus quite a few under Wine that would be a pain to have to reinstall

H/w-wise I have an HP with a Intel(R) Celeron(R) D CPU 3.20GHz
 and onboard graphics.

---

### Post by eastwood_systems on 2011-10-16
The following just worked for me:
1)  Boot into recovery mode.
2)  sudo apt-get clean
3)  sudo apt-get update
     This failed, but the error message provided details on a dpkg command that needed to be run.  I ran that command, and then the update command again.
4)  sudo apt-get upgrade
5)  Exit and reboot as normal.

---

### Post by sumithar on 2011-10-16
> **eastwood_systems said:**
> The following just worked for me:
1)  Boot into recovery mode.
2)  sudo apt-get clean
3)  sudo apt-get update
     This failed, but the error message provided details on a dpkg command that needed to be run.  I ran that command, and then the update command again.
4)  sudo apt-get upgrade
5)  Exit and reboot as normal.

I tried to boot into the kernel 3.0.12 recovery mode.  I got a screen full of text with this line at the bottom
0.772599] [<c1533b7e>] kernel_thread_helper + 0x6/0x10

and it hanged with the caps lock and scroll lock lights flashing.

I had to switch it off.

---

### Post by garvinrick4 on 2011-10-16
Take your install cd and boot off of it and hit space bar when you see the icons on
bottom right at the start.
Choose install
when get to screen that asks you how to install click on "something else"
Now when get to screen where shows partition table double click on sda1 that is your
linux install correct.
then go ext4 format, check the format box, mount point is /
You already have a swap do not need another one.
On bottom of same page make sure "boot loader" (grub) is going to sda not sda1 but sda
Now finish install.
Only thing effected is sda1 will get a fresh install all other partitions not being touched. (Just focus while installing)

---

### Post by sumithar on 2011-10-17
> **garvinrick4 said:**
> Take your install cd and boot off of it and hit space bar when you see the icons on
bottom right at the start.
Choose install
when get to screen that asks you how to install click on "something else"
Now when get to screen where shows partition table double click on sda1 that is your
linux install correct.
then go ext4 format, check the format box, mount point is /
You already have a swap do not need another one.
On bottom of same page make sure "boot loader" (grub) is going to sda not sda1 but sda
Now finish install.
Only thing effected is sda1 will get a fresh install all other partitions not being touched. (Just focus while installing)
This was the kind of directions I was hoping to get.  
I followed these steps and installed Ubuntu.  When I took out the CD and restarted I got a black screen which said file error and a grub-rescue prompt.

I googled this and applied these instructions
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Now it booted up into a black screen with just the prompt 
grub>
Then I followed the boot repair instructions on this page
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and did everything they asked.

Now it boots up into a screen which says on the top

GNU GRUB version 1.99~rc1-13ubuntu3
Minimal bash like editing is supported. Some other stuff and then a prompt
grub>

the only difference, this is not a black screen but with the ubuntu pinkish-purplish background.

Any thoughts?

---

### Post by garvinrick4 on 2011-10-17
I believe your install is in sda1,  [COLOR=Red]not sda5[/COLOR] it is swap partition.
In live Cd (install cd using Try Ubuntu) Copy and paste these one at a time.
```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
```
sudo reboot
```

---

### Post by sumithar on 2011-10-17
Oh- I did have sda1 not sda5 when I typed in those commands- I just pasted here what was on the website by mistake.  I changed it when I entered it.

FWIW, I redid it, this time including the umount command.  I got an installation successful after the 2nd command.

But after I reboot I am now at a black screen with the GNU GRUB version blah blah and a grub> prompt.

---

### Post by garvinrick4 on 2011-10-17
Ok run these: 
This gets into your file system and  installs grub from there, if this does not work than need to run
a bootscript as per link at bottom. In other words there is other problems if this does not work or you installed in a different partition than sda1.
```
sudo mount /dev/sda1 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```Hopefully you are working and do not need this but if you do only takes a minute to run. Need any help running this
just ask.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by youngunix on 2011-10-17
You should really save yourself all this time consuming methods and just save all the important data onto a separate storage device and do a fresh/clean install.

---

### Post by garvinrick4 on 2011-10-17
> You should  really save yourself all this time consuming methods and just save all  the important data onto a separate storage device and do a fresh/clean  install.
It is a clean install??? boot loader did not get into mbr at install. One step at a time the worst that could
happen is "OP could  learn something", nothing wrong with that at all. Maybe someone reading Thread
could also learn something new, nothing wrong with that either. Some have a thirst and some do not.

---

### Post by sumithar on 2011-10-18
> **garvinrick4 said:**
> Ok run these: 
This gets into your file system and  installs grub from there, if this does not work than need to run
a bootscript as per link at bottom. In other words there is other problems if this does not work or you installed in a different partition than sda1.
```
sudo mount /dev/sda1 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```Hopefully you are working and do not need this but if you do only takes a minute to run. Need any help running this
just ask.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

Hi 
Thanks for your continued patience.  I followed those instructions and after booting I do see a grub menu.  But if I choose the 1st option (kernel 2.something) I get a black screen with my CapsLock and ScrollLock lights flashing.  If I hit enter, the flashing stops and nothing.

If I choose option 2, recovery, then I get a screen full of text like I have described earlier and then nothing.

So I tried the bootinfo thing.  Attached is the RESULTS.txt.

Again- I'm so glad that you are with me on this!

---

### Post by garvinrick4 on 2011-10-18
You installed Natty.
sda1 is / with boot files. 
sda3 is in ext4 but not as /home just a partition formatted in ext4. (has boot files in it installed there by accident at one time or another.) easier to just reinstall since a fresh install.
Lets reinstall to get / and /home installed correctly.

#Put install Cd or usb in and boot off of and hit spacebar soon as icons come up on bottom right at start.
and hit install Ubuntu.
#Install again choosing "something else"
Answer questions until you get to partition table screen.
Double click on sda1
sda1 as format ext4 and check format box and mount point at /
done there.
Now double click on sda3
choose format at ext4, check format box and mount point at /home
Make sure on bottom of same page bootloader to install in sda
already have a swap no worries there.
Finish install and now boot into Natty or Oneiric according to which install cd you have

---

### Post by sumithar on 2011-10-20
> **garvinrick4 said:**
> You installed Natty.
sda1 is / with boot files. 
sda3 is in ext4 but not as /home just a partition formatted in ext4. (has boot files in it installed there by accident at one time or another.) easier to just reinstall since a fresh install.
Lets reinstall to get / and /home installed correctly.

#Put install Cd or usb in and boot off of and hit spacebar soon as icons come up on bottom right at start.
and hit install Ubuntu.
#Install again choosing "something else"
Answer questions until you get to partition table screen.
Double click on sda1
sda1 as format ext4 and check format box and mount point at /
done there.
Now double click on sda3
choose format at ext4, check format box and mount point at /home
Make sure on bottom of same page bootloader to install in sda
already have a swap no worries there.
Finish install and now boot into Natty or Oneiric according to which install cd you have

Yes, as you point out there was some kind of linux install on sda3 as well which must have messed up grub.

Thanks to your detailed steps I have a working Natty system now.
I have 2 questions
a) How can I reinstate my user files?  I did back up my user directory prior to reformatting sda3.  When reinstalling I created a user with the same name.  Do I have to boot again from CD and overlay the "new" user directory with the backed up one?  Or can I create a 2nd user, boot into that user and then do this?

b) If I reinstate my user files, will my installed programs be now available?  How about the windows executables under Wine?

Again,  you have been very kind and I've learnt in this process...

---

### Post by garvinrick4 on 2011-10-20
> a) How can I reinstate my user files?  I did back up my user directory  prior to reformatting sda3.  When reinstalling I created a user with the  same name.  Do I have to boot again from CD and overlay the "new" user  directory with the backed up one?  Or can I create a 2nd user, boot into  that user and then do this?When I first started Linux I would have backed up /home and copied each directories contents
back into new install. Nowadays I have a seperate /home partition so never have a problem
with /home contents, of course keep a backup but been a while since had to use.
> b) If I reinstate my user files, will my installed programs be now available?  How about the windows executables under Wine?
 Have never used Wine so do not know. There is away to copy installed and back into
new install using a dpkg command I do believe but never found it necessary for me to use I have 
done so many installs downloading packages I use is like second nature. Maybe another
user adept in this will chime in and help you with these questions, enjoy your Ubuntu sumithar

---

### Post by lpietsch on 2011-10-21
Same type of error here: upgrading to Xubuntu Oneiric; afterwards every boot attempt hangs at same point as described by earlier posters. I looked at the logs in my /var, and found that /var/log/installer/syslog was full of warnings talking about a failure to load some driver for an Nvidia graphics card (the installation process had not alerted me to these problems). Then, /var/log/Xorg.0.log seems to contain the error messages relevant to the boot failure, and they are also related to problems with the Nvidia graphics card driver. The Xorg log stops with a message "Fatal server error: no screens found".

Haven't figured out how to solve this yet; right now it seems I can't even log into Grub. Making a clean reinstall (reformatting the root partition, keeping a /home partition untouched) doesn't solve the issue for me either.

---

### Post by lpietsch on 2011-10-21
Update: I think I solved this at least on my system. I had to change the Grub configuration to make Linux boot with the "nomodeset" option. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for instructions and a bit of an explanation.

---

### Post by sumithar on 2011-10-22
> **lpietsch said:**
> Update: I think I solved this at least on my system. I had to change the Grub configuration to make Linux boot with the "nomodeset" option. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for instructions and a bit of an explanation.
Thanks- but I had already followed instructions to reformat the old "home" partition as well as the "/" partition.  I wish I had seen this earlier tho', I might have given it a whirl rather than formatting "/home" as well.

---

### Post by sumithar on 2011-10-22
> **garvinrick4 said:**
> When I first started Linux I would have backed up /home and copied each directories contents
back into new install. Nowadays I have a seperate /home partition so never have a problem
with /home contents, of course keep a backup but been a while since had to use.
 Have never used Wine so do not know. There is away to copy installed and back into
new install using a dpkg command I do believe but never found it necessary for me to use I have 
done so many installs downloading packages I use is like second nature. Maybe another
user adept in this will chime in and help you with these questions, enjoy your Ubuntu sumithar

Again, thanks for holding my hand thru this.  I tried overwriting the newly created user directory with my save one but it led to all kinds of funny problems.  So I deleted that user, recreated it and am now selectively copying over the saved stuff like Downloads, Documents and so on.

My biggest pain point was getting Firefox back to the way it was with the plugins and extensions and so on.

My torrents are also messed up since I don't have ratio information anymore on the ones that were in progress.

But overall, doing OK.

I will hold off on Oneiric for another 6 months or so and hope bugs get ironed out.

---

