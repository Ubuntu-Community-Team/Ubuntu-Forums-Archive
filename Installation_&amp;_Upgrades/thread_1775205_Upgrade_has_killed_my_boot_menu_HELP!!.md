---
title: "Upgrade has killed my boot menu?? HELP!!"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by MikeSz on 2011-06-04
Hi All - I know there are posts about this though Ive read it, and tried what it suggests and its not seeming to work!
Ive just upgraded to 11.04 using the update manager and now ive no boot menu and when I restart I just get a message on my monitor that says "out of range"
Ive tried Shift+alt+f7, ctrl+alt+f1 and pressing shift on startup.  Ive also followed the advice on a help thread on here to edit /etc/default/grub and comment out GRUB_HIDDEN_TIMEOUT=00 (except on mine there was only one '0' and it was already commented out!!) and now im completely stuck.

Can anyone help?  Im running in the live CD environment at the moment

---

### Post by oldfred on 2011-06-04
Have you held shift key from BIOS until menu appears. Just tapping it does not work, it seems.

I also have had it recognize down arrow to change boot in menu even when you never see menu. Try one down and see if you can boot recovery.

What video card do you have. Did you have any special video settings in your grub settings?

---

### Post by MikeSz on 2011-06-04
Will try those now.  Not sure about graphics settings, I didnt mess about with grub if thats what you're asking?

---

### Post by MikeSz on 2011-06-04
Nope, holding down either shift or the down arrow made any difference.

It still just gives me a "out of range" message

P.S. - im not on my mac - this is a normal PC.

Just out of curiosity - Im running a 10.04 live CD, would just installing this version again cure it?

---

### Post by oldfred on 2011-06-04
I do not know the out of range message, but something in Video is set wrong, whether it is grub or Ubuntu I am not sure.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Above discusses GRUB_GXFMODE, do you have that in your grub settings?

---

### Post by MikeSz on 2011-06-04
I had a read through this though none of it seemed to work.  got to step one on the troubleshooting flow chart and couldnt go passed that as shift doesnt do anything.

would this work on my system and get me a grub menu back? [http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

On the query of the grub settings, im not sure what you mean, what do I need to check?

---

### Post by oldfred on 2011-06-04
Look in this file, but from liveCD I think it also has to be a /media at the front.

gksudo gedit /etc/default/grub

My Maverick grub has everything commented out (# at beginning of line)

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by MikeSz on 2011-06-04
Ive got this...[http://paste.ubuntu.com/618444/](http://paste.ubuntu.com/618444/)

Ive added the comment in front of GRUB_HIDDEN_TIMEOUT=0 though dont know how to run update-grub like it says at the top as when I do, I get this...

ubuntu@ubuntu:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

UPDATE - anyone know how to rerun grup-update?  I cant seem to see how to do it and the guide doesnt explain how you do it, it just says this...

[I]Step 1. Do you have a Grub Menu?
- Yes: Go to step 2...
- No: Whiie booting, Press shift key (don't hold down) multiple times to see if the Grub menu will come up
- - If yes on Menu, go to step 2
- - If no, comment out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00. and rerun grub-update (from a LiveCD)
- - - If yes on Grub Menu go to Step 2
- - - If No, reinstall grub and Start Step 1 from Beginning... Becuase it seems that Grub is not booting.
[/I]

---

### Post by oldfred on 2011-06-04
You cannot run an update-grub from a liveCD unless you chroot into your install. 

This is one time where you edit the grub.cfg even though it says do not edit. It is also write protected and I forgot how to change that.

modify this to the correct location or cd to where it is:
sudo chmod +w /media/boot/grub/grub.cfg

Then 
gksudo gedit /media/boot/grub/grub.cfg

See Manual Editing of grub.cfg
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by MikeSz on 2011-06-04
Thanks for the help - though I think im really strugling here.  Ive tried the commands and I just get this...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo chmod +w /media/boot/grub/grub.cfg
chmod: cannot access `/media/boot/grub/grub.cfg': No such file or directory
ubuntu@ubuntu:~$ sudo chmod +w /boot/grub/grub.cfg
chmod: cannot access `/boot/grub/grub.cfg': No such file or directory
ubuntu@ubuntu:~$ gksudo gedit /media/boot/grub/grub.cfg

when the file opens, theres nothing in it - its just a blank document!

Ive also tried reading the link you gave me but its way too complicated for me, ive tried some of the things on there and they dont seem to work either.

Im actually getting quite panicked now and just need to fix it - Im running the live CD at the moment, version 10.04 - if I run the installation again from the live CD will it just replace the everything and put everything back to a previous version?  If so, I think I might do that

---

### Post by MikeSz on 2011-06-04
Getting really very nervous now, can anyone please help with this?

Ive been thinking - could I just delete all the linux partitions and install 10.04 from the live CD?  Ive attached what I have at the moment, though theres also a spare drive which you cant see which is 160gb of pretty much unused space although its been allocated /dev/sdb5 for some reason

If I delete everything apart from /dev/sda1, will I then be able to install ubuntu from scratch, have it pick up the windows partition, reinstall everything including a working boot menu and I can be back to where I was?  Theres nothing particularly in the linux partitions that I cant replace

---

### Post by kansasnoob on 2011-06-04
Would it be possible for you to DL and burn the disc recommended in step #1 here:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

If so, and if that gets you booted, you could try following the rest of those steps and see what happens.

NOTE: Please ignore the rest of that thread. I just needed a place to stick those instructions so I didn't have to redo it each time.

---

### Post by MikeSz on 2011-06-04
thanks for that - I had tried this before, unfortunately im running the live cd and for some reason it doesnt seem to like me (a) downloading large files (b) ive no drive to burn the discs to as the live cd is in the cd drive

CHECK THAT - ive downloaded it, and it says I can put it on a floppy - could you tell me step by step how I do that please?  

Many thanks for all the help - it is appreciated!

---

### Post by oldfred on 2011-06-04
I am sure you cannot put it on a floppy, but if your system is new enough to boot USB flash drives you can install it to that.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by MikeSz on 2011-06-04
darn it - my system isnt new enough for usb!!

---

### Post by oldfred on 2011-06-04
While it seems like video issues run this from liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by MikeSz on 2011-06-04
Thanks for all the help guys - in the end I've given up, deleted all the linux partitions and reinstalled from the live CD (gone back to 10.04) and its all working now.  

thanks again - think il be leaving 11.04 for the time being!!!

---

