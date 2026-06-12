---
title: "installing Windows with Ubuntu already there"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by TKM625 on 2006-07-19
I need to have Windows installed, but I've already got Ubuntu on my main hard drive. I've got another hard drive that has nothing on it. How would I go about this? I've heard it's a living hell to get working, and that you should install Windows first, but I've already got Ubuntu running, and I haven't needed Windows until now.

---

### Post by catlett on 2006-07-19
If you have another hard drive it is relatively simple to dual boot even with installing windows second.
Disconnect your Ubuntu hard drive and connect the new hard drive. Make sure you have the jumpers correct. Right now the windows drive should be set as master. After the install it will be switched to slave.
Once the drive is in, boot to the XP install disk. The installer is simple. Just give it the whole drive. The installer is entirely graphical and the most work you will do is activating and registering. If you have an internet connection, this can all be done online as you install.
After the install is done, put the Ubuntu drive back in. THIS IS IMPORTANT. Make sure Ubuntu is the Master and Windows is the slave. Hard drives usually have a diagram on them that shows the jumper position for master and slave.
When you start up you will get your regular grub menu and it will only show Ubuntu. What you have to do is edit the Grub menu list and put in an entry for windows.
Open a terminal and put this command in 
```
sudo gedit /boot/grub/menu.lst
```
When the text document opens go to the bottom. Hit enter a couple of times to put some space between the last entry and this entry. Enter this in the document
```
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
Make sure to hit save at the top of gedit's window. That is it. As long as the drives are IDE and not SATA this will work.
The trick is the map section. Windows likes to be the first hard drive.You can trick it into thinking it is the first drive with the mapping entries in grub.
When you restart there will be a windows entry and you will be able to select it and boot into windows.

---

### Post by TKM625 on 2006-07-19
Awesome, thanks a ton. :D

---

### Post by patsissons on 2006-07-20
how would one go about installing windows onto an empty ntfs drive on a one disk system without borking the boot manager?

The only thing I can think of off hand is to do the windows install then boot to a live cd and dpkg-reconfigure the boot manager package (grub-disk?).  I would rather hear from experience than go out on a limb, so if anyone knows more specific details on this type of procedure please fill in the blanks :)

---

### Post by catlett on 2006-07-20
Re-installing grub from a live cd is not perfect. I would do it like this.
Create your partition for windows. Just make sure it is a primary partition. (you can only have 4 primary partitions. I don't know how many you already have. Ubuintu doesn't need a primary but windows does)
Next run the XP inmstall. This will erase part of grub. Part of grub is on the mbr, the rest of grub is in your boot folder. The bad part is grub will not work without the mbr part.
The issue now is, windows canboot but ubuntu is now on an unaccessable partition.
I would use GAG to boot to Ubuntu. It is a small application. You download it and either install it to a floppy or you can burn the iso to a cd and boot to it.  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
Once you get back into your regular ubuntu desktop. Open a terminal and enter ```
sudo grub-install /dev/hda
```
This will install grub to your mbr again. Windows should be recognised. If nbot first run grub update  ```
sudo update-grub
```
If that fails you can add an entry for windows in your grub menu.
```
sudo gedit /boot/grub/menu.lst
```
When the document opens add the entry for windows at the bottom.

```
title              Windows XP
root               (hd0,?)
makeactive
chainloader        +1
```
The question mark is because I don't know what partition windows is going to be on. Grub gives 0 a value. So the first partition is 0, the second is 1 and so on. Your entry will start with h0 because it is the hard drive and it is the first hard drive, The question is what partition windows will be installed on. I do not think you will need a mapping entry for your boot. It is needed when windows is on the slave drive

---

### Post by miguelito928 on 2006-07-20
Let me ask this question then...

I have a dual-boot setup with my primary hard drive between Ubuntu and XP.  I just got a hold of Vista Beta 2 and wanted to put it on a second hard drive to play around with it.  As I was reading this post I figured the first solution proposed was my answer.  However,  as I read on I realized that you were doing the mapping thing and that that won't work to have two Windows installations on different hard drives.  I'm assuming you can't fool both Windows installations into thinking they are on the first hard drive.  Is this true?  Thanks.

miguelito928

---

### Post by catlett on 2006-07-20
I don't have any experience with 2 installs of windows BUT the mapping is only directed at the OS you are boting.
It is a bootloader trick, not a hard drive trick.
So you could try it, it may work.
If not you could also try GAG. The link is in an above post. 
Just remeber that grub places a value on 0. So the first hard drive is 0 and the second drive is 1. In case you want more grub information, this is the grub manual [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by patsissons on 2006-07-21
Just a question, why won't running
```
sudo grub-install /dev/hda
```
work from a live cd?

---

### Post by catlett on 2006-07-21
Grub has to read your bios. When you run from a live cd grub can't do it. It gets confused because the live session is run off the cd drive and it returns an era when searching for the bios.
This is the one area where grub really lacks. It is not easy to install without being logged in the system you want to install it on. What I do is, I install grub to a floppy during installationm. This way I have a failsafe way to boot into my system. Once I boot in to the system from the floppy, I run grub-install to install grub to the mbr. That way grub is installed and I have a floppy backup in case grub somehow gets erased.
There was a how to a while back that said to mount your partition and then cd to it, chown or chroot and then run grub install. It didn't work for me. Plus I didn't know anything about linux then and I can't find the how to now to to see if I understand the commands better now that I have some experience.
This is supposed to work from a live session.
Supposedly you can install from a live cd with these commands, but I have not gotten a successful grub reinstallation from a live cd.
open a terminal.
```
sudo grub
```
This willl give you a grub< prompt. Now enter 
```
find /boot/grub/stage1
```
Remember what it answers, and use it here (I'll asume it is (hd0,1))
While still at grub< enter
```
root (hd0,1)
``` Next command puts it on the mbr, so just use the first number from the find answer
```
setup (hd,0)
```
```
quit
```That is supposed to work but I do not have any proof. You can try it before you attempt gag.

---

### Post by patsissons on 2006-07-25
I can confirm that this works, I couldn't get find to work, but maybe I should have chroot'd my mounted partition instead of trying to find it where is was mounted.  However, I was still able to make this work as I only have one hard drive and I know which partition is my root.

Thanks for the help.

p.s. I have also read about people mounting, chrooting, and sudo grub-install /dev/xdx.  It seems like this should work, but the trouble is that you chroot'd /dev will not contain your hard drive node.  I think maybe you could mount --bind it to dev, but I didn't think of that at the time (plus you would have to move your chroot'd dev elsewhere for the time being).  perhaps if someone else is in a similar situation they can give that a shot because it seems as though grub-install is a much more trivial task.

---

### Post by catlett on 2006-07-25
> **patsissons said:**
> I can confirm that this works, I couldn't get find to work, but maybe I should have chroot'd my mounted partition instead of trying to find it where is was mounted.  However, I was still able to make this work as I only have one hard drive and I know which partition is my root.

Thanks for the help.

p.s. I have also read about people mounting, chrooting, and sudo grub-install /dev/xdx.  It seems like this should work, but the trouble is that you chroot'd /dev will not contain your hard drive node.  I think maybe you could mount --bind it to dev, but I didn't think of that at the time (plus you would have to move your chroot'd dev elsewhere for the time being).  perhaps if someone else is in a similar situation they can give that a shot because it seems as though grub-install is a much more trivial task.

Great! I was hoping someone would know if that worked. I have been meaning to run fixmbr to restore ntdlr and then boot to a live cd and try to get grub to install but I have been too lazy
.
So if I am understanding you correctly, you booted to the live cd. You did not get a return from find grub/stage1 but you knew where your root partition was.
Using the partition you knew root to be on you then ran (For sake of example I will use (hd0,1) as your root)
```
sudo grub
```
Then at the grub prompts you entered
```
root  (hd0,1)
setup  (hd0)
quit
```And that installed grub to your mbr from the live cd?
That is great. I found that in a mempis how to but I couldn't find it again.
I then saw a section in the grub manual about setup (hd0) but it didn't mention using it in a live cd.
I was hoping it would work but I never knew for sure. The only thing I use to see on Ubuntu was a how to from Breezy 5.10 It said to run the installer and select the same partitions but do not select to format. It will give an error and then if you continue it will take you to a menu. If you scrolled down there was a section to the install menu that said "install boot-loader". You were then to select that and grub would install.
I thought to myself, there has to be a way to install grub without using a "trick"
I could never find one. The only one was the one I mentioned earlier but it was over my head at the time and I tyhought nothing of it, until I went looking for it and couldn't find it.
Anyways thanks for posting your results. I am glad there is finally a straight forward way to install grub from a live cd.

---

### Post by patsissons on 2006-07-27
actually, I think there was just a typo when i tried to find the root partition.  I was testing out the vista beta (BLEAH!), and have since reinstalled XP.  The second time find worked without any problems.  So to sum up
```

sudo grub
find /boot/grub/stage1
  <returns (hdx,y)>
root (hdx,y)
setup (hdx)
quit

```
this can all be done from a live cd boot (i used the dapper x64 disc, but I'm sure it works with most other live discs as well).

Now that I have windows installed (quite an ordeal, my bios didn't support my sata drive correctly when installing windows) and grub back on my mbr there is only one thing left to figure out.  That being how to get an entry into my menu.lst for windows.  I know that I could easily just add in the 5 or 6 lines of grub code to add windows to my boot list, but this is no good.  When I grab the latest kernel image, which happens quite often, my menu.lst will reset back to where it was before (unless I am missing something).  Any ideas on how to make ubuntu persist my windows entry into grub?  I have read that adding it after the "### END DEBIAN AUTOMAGIC KERNELS LIST" will help persist, but I won't find out until the next kernel update.  is this true or is there a better way to do this?

---

### Post by Herman on 2006-07-27
I can confirm that (in my computer at least) adding the Windows entry above the Ubuntu entries in the automagic kernels list will cause it to be deleted during a kernel update. I have tested this myself, after helping someone else get their Windows entry back after theirs was lost. It's true!

If Windows is detected in the computer when Ubuntu is installed, Grub places Windows under the divider at the bottom of the automagic kernels list, and that is the right place for it. Some people cut it and paste it to the top of the automagic kernels list as an easy way to get Windows to be the first boot preference.
The correct way to set the default operating system is this way, [*click here.*]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

Below is a sample of the bottom section of a typical menu.lst file.
>                     ## ## End Default Options ##
                         
                   title        Ubuntu, kernel 2.6.15-25-386
                   root        (hd0,1)
                   kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
                   initrd        /boot/initrd.img-2.6.15-25-386
                   savedefault
                   boot
                         
                   title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
                   root        (hd0,1)
                   kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
                   initrd        /boot/initrd.img-2.6.15-25-386
                   boot

                   title        Ubuntu, memtest86+
                   root        (hd0,1)
                   kernel        /boot/memtest86+.bin 
                   boot
                         
                   ### END DEBIAN AUTOMAGIC KERNELS LIST
                         
                   # This is a divider, added to separate the menu items below from the Debian
                   # ones.
                   title        Other operating systems:
                   root
                         
                         
                   # This entry automatically added by the Debian installer for a non-linux OS
                   # on /dev/hda1
                   title        Microsoft Windows XP Home Edition
                   root        (hd0,0)
                   savedefault
                   makeactive
                   chainloader    +1  You can copy the bottom twelve lines from here and paste it at the bottom of your own menu.lst if you like. Then edit it to suit you needs. 
If Windows in your machine is other than (hd0,1), it will need the partition number edited. You will also need to add map commands if Windows is on a non-first hard disk in your machine. 
You can replace the words, 'Microsoft Windows XP Home Edition' after the command; title with anything you like, that line doesn't affect anything except the words you will see on that line in your Grub menu.
I would guess the next four lines under where it announces the end of the Debian automagic kernels list could be important, especailly the ones without the '#' (comment symbol), although I have not tried deleting  them to see what happens when I don't have them. You might need those. That's the main reason for my post.
Regards, Herman :D

---

### Post by catlett on 2006-07-27
Since you are here Herman, I'll bother you with a question :D 
I always told people to get windows to be the first choice by changing 
```
default         0
```
to the number windows was in the list.
Someone posted that after a kernel update windows would change it's place in the list and the number for "default" wouldn't coincide with windows. So they recomended to put windows at tyhe top and keep the default 0.
But now you are saying that the entry deletyes during a kernel upgrade.
I am assumiomg that keeepmig windows at the bottom is correct buit do you have to change the default value everytime the kernel upgrades?

---

### Post by Herman on 2006-07-27
Hello there, catlett! That is an interesting point you are making, I probably didn't leave Windows as the default boot preference in my computer for long enough to notice that. 
I will do a test to find out more about that sometime soon. (I know someone who has that preference set who might be due for an update, so I will be able to see for myself what will happen.)
For now all I can say is, I normally comment out and eventually delete my extra (old) Ubuntu kernel entries in any case. If people do that, they will be able to leave their set default as it is. 
Regards, Herman :D

---

### Post by confused57 on 2006-07-27
> **Herman said:**
> Hello there, catlett! That is an interesting point you are making, I probably didn't leave Windows as the default boot preference in my computer for long enough to notice that. 
I will do a test to find out more about that sometime soon. (I know someone who has that preference set who might be due for an update, so I will be able to see for myself what will happen.)
For now all I can say is, I normally comment out and eventually delete my extra (old) Ubuntu kernel entries in any case. If people do that, they will be able to leave their set default as it is. 
Regards, Herman :D

Herman,  couldn't you place the Windows entry ABOVE(not at the top of) the BEGIN AUTOMAGIC KERNELS LIST?  This way you could leave the default as 0 and it wouldn't be affected by kernel upgrades...this was suggested to me by lha when I was setting up a dualboot of Windows with 2 hard drives:


[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I've had 2 kernel upgrades in both Dapper & Breezy and haven't had to change the default from 0, my system continued to boot Windows first(by default) after the updated kernels.

---

### Post by Herman on 2006-07-27
confused57, Thanks, I didn't know that. That's a good idea and if lha suggested it and you've tested it I wouldn't dispute it. It would be simpler to explain to new users what they need to do with that method too.
That's a great how-to that you made as well, I like it.
Regards, Herman :D

---

### Post by confused57 on 2006-07-27
> **Herman said:**
> confused57, Thanks, I didn't know that. That's a good idea and if lha suggested it and you've tested it I wouldn't dispute it. It would be simpler to explain to new users what they need to do with that method too.
That's a great how-to that you made as well, I like it.
Regards, Herman :D

Thanks Herman, I really respect your opinion, especially for your excellent website and all the help you give to people.
The method has worked for me with 2 hard drives, but I would think it would also work dualbooting Windows & Ubuntu on one HD.  As I mentioned, I've never had to change the default from 0(to boot Windows by default), even after 2 kernel updates on both Breezy & Dapper.  I've been hesitant to suggest it to users dualbooting with one HD, since I don't have any experience with that method.

---

### Post by Herman on 2006-07-28
I respect you fellows too, (and others who contribute to these forums). I haven't yet gone to the expense and made the effort to install more than one hard disk in a computer, so I can only learn about configuring grub for that by reading whatever I can find. I have learned a lot from you (confused57) and lha's threads and posts on that subject.

I was just  checking [what the Grub manual has to say about the default number]("http://www.gnu.org/software/grub/manual/grub.html#default"), and I see that we can also delete the number there and type in the word 'saved' instead of a number.  ```
default saved 
```  That might be even easier again! I haven't tried that trick yet, I'll give that one a go and see how well it works.
Regards, Herman :D

---

### Post by catlett on 2006-07-28
Hello everyone,
Herman, just to add to the savedefault topic.
Here is the section you linked to 
```
Save the current menu entry or num if specified as a default entry. Here is an example:

          default saved
          timeout 10
          
          title GNU/Linux
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault
          
          title FreeBSD
          root (hd0,a)
          kernel /boot/loader
          savedefault
     

With this configuration, GRUB will choose the entry booted previously as the default entry.

You can specify `fallback' instead of a number. Then, next fallback entry is saved. Next fallback entry is chosen from fallback entries. Normally, this will be the first entry in fallback ones. 
```It appears that "savedefault" tells grub to boot the last entry chosen from the menu and booted to, something similar to Ubuntu's session. Unless you specify a different session, the last session loads after login.
I believe (please tell me if I am wrong, that is why I am posting) this is how this would work. If you replaced "default   0" with "default saved", then the last OS booted will boot next startup.
This actually solves the kernel upgrade problem. The last entry gets booted to after the kernel upgrade. It doesn't matter what number it is in the order because grub isn't using a number to associate it to the savedefault.

My only question is, "Do you have to write "savedefault" in every entry, or only the entry or entries you want to be considered for defaulting to?"
 I couldn't find any further explanation in the manual.

---

### Post by Herman on 2006-07-28
> My only question is, "Do you have to write "savedefault" in every entry, or only the entry or entries you want to be considered for defaulting to?"
 I couldn't find any further explanation in the manual. Well all my menu.lst files in the computers here seem to have the command 'savedefault' in each operating system entry aleady there by default. I presume other people's menu.lst files would be the same.
I don't see the command 'savedefault' in the entries for 'recovery mode', or 'memtest86+' though.
I think we'll just have to play around and run some experiments if we want to find out more. I wonder how it would work if I delete all the 'savedefault' commands in each entry but one of the one I want to set as the default O.S. and use the 'default saved' idea already decribed.
I do remember having to remove the 'savedefault' commands to get GRUB to work properly from a GRUB CD. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD"), and see step 3). Probably that would be because things (the last booted or default) can't be 'saved' to a CD like they can when Grub is hard-disk installed. So it follows (to my twisted logic anyway), that if we *deleted* the savedefault commands from the ones we don't want saved as the default, then the only one that has that command should be the one that will remain as th default operating system. That might be yet another way of achieving the same goal. (He-he :D) Regards, Herman

---

