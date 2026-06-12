---
title: "Ubuntu 18.04 hangs at boot with black screen, occasional flashing text"
date: 2018-07-08
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2018-07-08
I have a dual boot machine (for background please see my other thread titled "How to install 18.04 over 16.04 while preserving windows 10"). This is an AMD A8  processor with Radeon R5 graphics (no Intel). When I now boot into newly installed Ubuntu 18.04, I can't get to the login screen. What  happens is that booting simply stops at the Ubuntu logo, with the first  of these five Ubuntu splash screen dots filled. The login screen only  appears very briefly and then I see a black  screen most of the time, with  some text blinking up shortly from time to  time. I get the exact same problem in recover mode. I am very suspecious this is [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1727356]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1727356").  The bug report suggests I use recovery mode to turn off Wayland in the GDM configuration and then re-boot. This is where I am having trouble. I am attempting to bypass this bug by disabling "Wayland". How to do this is explained in the bug report (directions for this is reproduced below). I am having trouble getting into read/write mode. I can launch VI from the root shell and enter VI to make the change as explained but cannot save the changes. From the bug report:

"How to turn Wayland off? Key is to disable it in /etc/gdm3/custom.conf. Code ('WaylandEnable=false')  is already there, just commented out. Accordingly, to get the hardware  booting all up to the desktop, proceed as following (written from head,  so actual wording might be slightly different):

 - Turn the PC on.
- As soon as the Grub boot selection screen appears, use up and down arrows on the keyboard to select 'Ubuntu (recovery mode)'.
- Hit 'Enter'.
- After a while, another selection screen appears. Select 'Enable  Network', which happens to be a simple way to re-mount the boot disk in  read-write mode.
- Back on the same selection screen, select a root shell.
- Being at the root shell, enter 'vi /etc/gdm3/custom.conf'.
- Using arrow keys, navigate to the line reading '#WaylandEnable=false'.
- Make sure the cursor is over this first '#'.
- Hit the 'x' key once, the '#' should disappear.
- Enter ':wq'. This gets you back to the root shell.
- Type 'reboot' and hit Enter."

Things seem to go wrong when I select enter network (4th step above). This is supposed to "re-mount the boot disk in read-write mode". It seems that after this selection I do not get a prompt to select the root shell. Do I have to issue another command to get this to complete? When I get tired of waiting I do a ctrl-c which finally gets me to the root shell. But in read only mode. I really can't tell if I am in read only or read-write until I try to save the change I made in VI. Can anyone help me get into read-write mode in recovery so I can launch VI and bypass this bug. Many thanks!

Also, how do I tell these guys ( [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1727356]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1727356").) the problem may be related to relatively new AMD products too, not just Intel stuff. They are fixated on Intel! I'll know for sure once I turn disable Wayland from the boot sequence?

---

### Post by #&amp;thj^% on 2018-07-08
[s]First lets see how the file now reads>>>post back the output of:
```
gedit /etc/gdm3/custom.conf
```[/s]
[s]In the case that I'm not clear...Copy and paste all the text from gedit and paste it back here, using code tags.[/s]
I'm not able to stick around so I will give you an easy method to disable wayland.
1.Open terminal and run:
```
sudoedit /etc/gdm3/custom.conf
```
Now with the arrow up and down keys navigate to where it shows "#WaylandEnable=false" and remove when the blinking cursor is over the "#" and hit delete.
Now to save this use the keycombo <ctrl+o> that is a letter o not zero >>and to close hit <ctrl+x> and reboot.
I do not think this will solve your problem though, but I do hope it works as you had hoped.
I'm seeing a lot of AMD machines with problems as of late here in the forums.
Good Luck.

---

### Post by jgwphd on 2018-07-08
@1fallen - thanks for the assistance. I have question? Before I do this copy and paste, I assume I have to boot into recovery and use the root shell to launch gedit, but at this point I still haven't been able to login and don't have a fully functioning system. I think I can do a "copy" of the gedit output (by selecting the text and doing a ctrl-c - or is their another command I should use?), ...but "paste to where" and how do I get the copy of custom.conf off the machine as you requested. I'll have to take the copy to another working machine. I noticed the custom.conf file is not very big, so if necessary I can just copy if down and type it in. Any suggestions for how to do the copy and paste, especially the "paste" part and how to get the output off the machine in recovery mode? Many Thanks!

---

### Post by #&amp;thj^% on 2018-07-09
> **jgwphd said:**
> @1fallen - thanks for the assistance. I have question? Before I do this copy and paste, I assume I have to boot into recovery and use the root shell to launch gedit, but at this point I still haven't been able to login and don't have a fully functioning system. I think I can do a "copy" of the gedit output (by selecting the text and doing a ctrl-c - or is their another command I should use?), ...but "paste to where" and how do I get the copy of custom.conf off the machine as you requested. I'll have to take the copy to another working machine. I noticed the custom.conf file is not very big, so if necessary I can just copy if down and type it in. Any suggestions for how to do the copy and paste, especially the "paste" part and how to get the output off the machine in recovery mode? Many Thanks!

I'm very sorry, I was under the impression you could at least get to a TTY session.
Forget about the gedit request then>>as that will be useless at this point.
So I guess I need to know first>> can you get to a TTY session?
If so just follow my top post that is not stricken out. 
Now if you can not get to a TTY session then when booting in recovery mode>> select** "enable networking"** this will give you the needed read/write support to make the changes I show in my above post.
Now if you still can't achieve this>> I have in the past used my USB/DVD installer to make the needed changes. If this is what we are resorted to just let me know and i will try to help you with that.
EDIT: I keep forgetting to ask if you have tried booting to a older kernel.

**I see after you edited your first post you have already tried the "enable network" method so i will show how to use your Live Installer.**

When you boot to the live installer choose Try Ubuntu then when you are in the live session open your file manager and on the left click the drive with the broken install so it will mount.
Then navigate to **"/etc/gdm3/custom.conf"** _but don't open the file yet._
Now open a terminal and run:
```
sudo -H gedit
```
Now grab the "custom.conf" from your broken drive file and drop it in the blank gedit.
now make the change to "#WaylandEnable=false" so it now looks like:
```
WaylandEnable=false
```
Save it and close now you can reboot.
Please understand i mean nothing bad by this, but I really don't think this will help you with your problem.
But I'm impressed with your enthusiasm so I'm hoping this will work for you. :)
Good Luck

---

### Post by jgwphd on 2018-07-09
@1fallen ....I am nearing the limits of my "booting" experience at this point. Can you give me some directions on how to get to a TTY session in recovery mode (it's been a long time).  BTW, this is a dual boot machine with windows 10, if that is something we need to consider.

The last "few times' that I selected the network option in recovery and hit enter (which is supposed to "re-mount the boot disk in read-write mode" according the the referenced bug report info at [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1727356]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1727356").), I do not get a prompt to select the root  shell. After I got tired of waiting I did a ctrl-c which finally gets me to the root  shell (maybe I should have waited longer - approx 2 minutes). But after i make changes to the custom.conf file I find out I am still in read only mode, since I get errors trying to save the change I made in VI. 

I will make another attempt to get into read/write mode by selecting enable networking but wait a lot longer. BTW, there were three selections for recover with different kernal versions. I have tried all three with the same results. If you want. I can copy down and post the numbers. 

A related question/observation. I find it strange that in recovery mode there is enforcement of read/write privileges. Why? The reason you are in recovery is to fix a problem and you need to change something. Can you enlighten me on the logic here  :-)

---

### Post by #&amp;thj^% on 2018-07-09
Please just proceed with the instructions below the line, [B]I see after you edited your first post you have already tried the "enable network" method so i will show how to use your Live Installer.
[/B]
And use the Live Installer method I show for that. :)

---

### Post by jgwphd on 2018-07-09
BTW, I forgot to mention the available 18.04 recover modes that I used. You asked about that and here are the ones available (tried all three): 

4.15.0-23 generic (recovery mode)
4.13.0-46  generic (recovery mode)
4.4.0-130  generic (recovery mode)

OK, How do I use the live installer? Are there instructions somewhere? **(Ooops, you already told me. I hadn't notice you been editing your prior posts. Sorry for the confusion. I'll try the installer.... Thanks!**) Also, remember this is a dual boot machine and I can't afford to loose windows, which is my backup if Ubuntu stops working, which it has  :-)  ...I greatly prefer Ubuntu!

I also want to let you know I appreciate your assistance! **(I understand your skepticism ...but the problem symptoms are dead on to the bug report ...disabling Wayland is the best place to start IMHO) ....after that I am not sure what to do  :-)**

---

### Post by #&amp;thj^% on 2018-07-09
Any Luck with the edit form the Live Installer method?

---

### Post by jgwphd on 2018-07-09
I haven't tried it yet. I have been busy with other work to make a living, and now we have family visitors. This journey from 16.04 to 18.04, which I expected to take an hour, has been time consuming and I can't spend too much additional time on this now or "the boss" goes on the warpath. :-)  I am anxious to try it out too and I will get to this sometime over the next day or two. I am in a little bit of distracted mode at this point... Your patience and assistance is greatly appreciated.

---

### Post by oldfred on 2018-07-10
FYI
The recovery mode is read only, so you can run fsck. Partitions have to be unmounted or I guess read only to run fsck without issues. Often after an abnormal shutdown file systems get corrupted. Windows then needs chkdsk. Or make sure system if fully shutdown before rebooting.
And then it gives options for other modes, remount, enable networking, etc.

---

### Post by jgwphd on 2018-07-10
As directed I did the "try Ubuntu" option on the installation disk but I couldn't navigate to **"/etc/gdm3/custom.conf"** because it is not a directory, so I just went to the directory where custom.conf was located with a **"cd [B]/etc/gdm3" **[/B]and then used the command "**sudo -H gedit custom.conf**" which opened a window and I removed the # in front of the WaylandEnable=False statement. I then clicked on the Save button with NO errors. I "assume" this made the change. 

While still in "try ubuntu" mode with the installation disk I did a sudo fdisk -l  which listed my drives and the partitions on them. I then did a fsck /dev/sda6. Some information, size, etc was given but No error message showed up.

I then powered down and the started back up and got the same black screen with flashing text problem. I restarted again in recovery mode and went to the root shell, and entered  'vi /etc/gdm3/custom.conf' and the # symbol was back! Whatever I did with the try it installation disk didn't work or somehow there are two copies of this file, maybe I changed the one on the installation disk but not my hard drive.

I decided to try some of the other options on the recovery menu. I selected the Repair Broken Packages. I got a statement the
 
"EFI System Partition (ESP) not usable" 
followed by an error "Your EFI System (ESP) is not mounted at /boot/efi." - I don't know if this is a problem or not????

I went back to the recovery menu and selected "run in fail safe package mode" - I got some messages that went by quickly and then got kicked out. I tried again and I didn't see any error message (but not sure) and got kick out again.

I then selected FSCK check all file systems but then got a warning message about having to be in read-only mode and I needed to reboot to get there. I was thinking did I accidentally do something to put me in read/write mode???? 

I went back to the root shell. And, just for frustration sake, I went into vi again with system.conf. I tried to remove the # again and did a save :wq. And It worked! ....magic, I tell you  :-)    I couldn't believe it! ...so I actually rebooted back into recovery mode a "few times" and used vi to see if the # was really removed. vi showed it was no longer there. 

Now feeling lucky and with much hope I rebooted ....and alias the same problem.  ....you have to keep your sense of humor  :-)

What should I do now? I have so much time invested into this problem I would like to see it through. and, I have to admit this is a bit of fun learning more about Ubuntu and recovery. Again your patience and assistance are more than welcome!

BTW, is there a command that I can issue in the root shell to see if WayLand is really gone and I am using X11? Will command "echo $XDG_SESSION_TYPE" or "echo $DESKTOP_SESSION" tell me at this point while using recovery?

---

### Post by #&amp;thj^% on 2018-07-11
First I'm glad you finally got the edit to work. :) (You learned from that)
If I'm reading correctly with "sudo -H gedit" well that was not how I had it in the instructions I provided, but that is history now. ;)

At this point as much as I would love to help you see this through>> I just don't know how to advise you on this matter.
I had to go back and read your first thread when this begun, and along with the problems that a Upgrade can bring vs a Fresh Clean install that is the best preferred method. (Along with a good backup for the things you need)

And for this:
> "EFI System Partition (ESP) not usable"
followed by an error "Your EFI System (ESP) is not mounted at /boot/efi." - I don't know if this is a problem or not????

This is out of my skill level for your specs.
I have a HP machine that i just don't use the UEFI bios instead I use the legacy option, that said>> I also have NO Windows partitions to deal with so this is a plus for me.
EDIT:
>     BTW, is there a command that I can issue in the root shell to see if WayLand is really gone and I am using X11? Will command "echo $XDG_SESSION_TYPE" or "echo $DESKTOP_SESSION" tell me at this point while using recovery? 


I'm afraid not as there is no DE session running in that mode.

---

### Post by oldfred on 2018-07-11
If able to boot, I do not understand issues with UEFI. 
       Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  
    
Post these:
cat /etc/fstab
lsblk -f
sudo efibootmgr -v

---

### Post by jgwphd on 2018-07-11
Just an FYI, I *never got the # removed from custom.conf using the installation disk and gedit.* When I rebooted after the attempt using the installation disk the same problem occurred. That caused me to go back into recovery mode and I saw the # was still there when I looked using vi. While still in recovery mode, I decided to try some other recovery options and I selected "run in fail safe package  mode" - I got some messages that went by quickly and then got kicked  out. I tried again and I didn't see any error message (but not sure) and  got kick out again. This was strange and unexpected behavior so I proceeded to select other options from the recovery menu to see if they would help somehow *...my speculation is this attempt to enter fail safe mode somehow put me in R/W mode even though it didn't work and kicked me back to the root shell command prompt.*

I then selected FSCK check all file systems but then got a warning  message about having to be in read-only mode and I needed to reboot to  get there but I didn't reboot ( *I was thinking did I accidentally do something to put me in  read/write mode). *Instead, I went back to the root shell and vi again with system.conf. I tried to remove the # again and did a  save :wq. And It worked at that time. When I think about it ....network mode never worked right and neither did safe mode from the recovery menu. I am now thinking maybe this upgrade attempt is beyond help. 

I tried these commands:

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" -- got no such command and another line with Legacy boot on HDD stated 

cat/etc/fstab ---response: no such directory
lsblk -f and sudo efibootmgr -v  -- both had had output but I didn't see any error messages

I don't know how to copy and past (paste to where?) the output of commands and get them off the machine in recovery mode. So asking me to post things means I have to hand re-type the output. 

My strategy going forward: 
**Do a format and a clean install of 18.04 on the non-windows partition **(maybe I should have done this first, but after seeing the identical match to the bug report I was convinced, at the time, that I would do a reinstall and just wind up back at the same place - so far i spent a lot of time learning how to successfully edit files in recovery mode and learning how to turn off Wayland ...maybe useful information/skills  :-) ).

Is there anything I need to worry about so when I install 18.04 on my existing dual boot machine with a broken copy of 18.04 and windows? I just want to make sure I preserve windows as my back-up (I really don't use it much but I would like to keep it). I'll post the results tomorrow.

Again....my sincerest **THANKS** for all the assistance!!!

---

### Post by #&amp;thj^% on 2018-07-11
> **jgwphd said:**
> Just an FYI, I [I]never got the # removed from custom.conf using the installation disk and gedit
You didn't follow my instructions so yes it would have failed>>>but that's water under the bridge now. ;)

> **jgwphd said:**
> 
My strategy going forward: 
**Do a format and a clean install of 18.04 on the non-windows partition **(maybe I should have done this first, but after seeing the identical match to the bug report I was convinced, at the time, that I would do a reinstall and just wind up back at the same place - so far i spent a lot of time learning how to successfully edit files in recovery mode and learning how to turn off Wayland ...maybe useful information/skills  :-) ).

+1 >>>That is the best Idea here going forward.
> **jgwphd said:**
> 

Is there anything I need to worry about so when I install 18.04 on my existing dual boot machine with a broken copy of 18.04 and windows? I just want to make sure I preserve windows as my back-up (I really don't use it much but I would like to keep it). I'll post the results tomorrow.

oldfred will will be able to help you with that along with others here that do dual boot with Windows.
I just don't use Windows at all so I'm a bit dated with any relevant information. But I do know you can recover the space used by Ubuntu on the windows partition.
Good Luck and Best Regards

---

### Post by oldfred on 2018-07-11
Always best to fully back up Windows, even if not your main system, you paid for it.
Only use Windows to change size of NTFS partitions, but not to create Linux partitions.

If you already have an ext4 partition, you just can use Something Else install option and choose (change button) that partition, as ext4 & as / (root) for new install.

If UEFI more details in link below in my signature.

---

### Post by jgwphd on 2018-07-12
Hi oldfred, The problem is I bought a used machine with Windows 10 on it and I put on Ubuntu (probably 2 years ago - when 16..04 came out). I forgot how I did it before and I don't have a recovery disk or the windows install key. That's why I am being careful. I have to use it to update my motorcycle Bluetooth head set - they only support windows  :-(    

Just to be cautious (I have a Dell Insperion model 5555 (64 bit machine). The status is I already have both Ubuntu and Windows on this machine (I assume I don't need to do anything with making a new partition or any partition re-sizing, ...just find the broken 18.04 partition and re-install 18.04:
 
1 - I guess I need to go into Bios ...and how do I know "for sure" I am using UEFI or not?   --- or should I turn it off/on. What do you recommend?  I remember playing with these settings to get the Dell to find the CD/DVD drive and boot from it (because it came with windows and no Ubuntu). I am not sure what the "correct" settings are now. If I choose the wrong settings will Windows not work? 
 
2- Do I need to do something with the secure boot option? ...what is the correct secure boot setting? (aren't UEFI and secure boot related somehow?) 

3 - What is the existing Ubuntu partition name that I look for when I use the "something else" install option so I can direct the Ubuntu 18.04 to the correct partition. 

4 - Any other advice? 

Many thanks for your assistance.

---

### Post by oldfred on 2018-07-12
If computer orignally came with Windows 10 it must be UEFI. Only those updated from Windows 7 may be the old BIOS/MBR configuration.

If getting grub> terminal none of the normal Linux commands work. The grub terminal only has a few limited commands to try to manually boot.

Linux will be installed in a ext4 partition, the installer should see that and tell you what is installed there.

From live installer post the commands requested above.

---

### Post by kurt18947 on 2018-07-14
> **jgwphd said:**
> Hi oldfred, The problem is I bought a used machine with Windows 10 on it and I put on Ubuntu (probably 2 years ago - when 16..04 came out). I forgot how I did it before and I don't have a recovery disk or the windows install key. That's why I am being careful. I have to use it to update my motorcycle Bluetooth head set - they only support windows  :-(    
..................................................


I am not expert so take this for what it's worth. I have a similar situation, I need Windows to update some hardware - about 10 minutes every 28 days.  I think Windows 10 doesn't have an install key. When it's first installed it creates a hash of your hardware and stores that hash on Microsoft's servers. If you need to reinstall it checks for that hash and automatically activates. At least that's how one reinstall went. I don't know if Dell has its own reinstall/reactivation procedure or not. Does Windows 10 support creating a rescue disc? Another thought would be to image the Windows partition so you could restore to the state when the image was created. A few ways to cover yourself.

---

### Post by oldfred on 2018-07-14
I always recommend a full backup.

My one Dell system with Windows, I did a Dell backup & Windows backup which it suggested when I first booted. Then I did a full image backup with Macrium Reflect. All the backups took 3 days (ok, I        
had to go to store for more flash drives & DVDs). And Ubuntu installed in about 10 minutes.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm) 


       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by jgwphd on 2018-08-07
I did a clean 18.04 install along side of windows. It was quick and worked fine. I still don't know what went wrong with "upgrading" from 16.04 to 18.04. I guess in my opinion I wouldn't recommend upgrading. I would say, just do a clean install. Thanks to everyone for their assistance.

---

### Post by notmarrco on 2018-08-28
Hi,

I had the same problem with my ubuntu 18.04 (migrated from 16.04).

I tried to follow @jgwphd tutorial, and I failed at the same steps in the "recovery mode". (ie activate network stalls and doesn't give the first screen back to allow to chose "root console").

But then I just booted in recovery mode, chose "root console" , and in root console I was able to simply :

```

sudo mount -o remount,rw /partition/identifier /mount/point

```
(for more info see : [https://askubuntu.com/a/175742](https://askubuntu.com/a/175742) )

Then with the filesystem mounted rw I was able to complete the tutorial and uncomment the "Wayland" line. And since then everything works !

Hope this helps !

---

