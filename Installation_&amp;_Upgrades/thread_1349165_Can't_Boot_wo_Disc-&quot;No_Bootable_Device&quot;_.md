---
title: "Can't Boot w/o Disc-&quot;No Bootable Device&quot; after removing Windows"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Uadebisi on 2009-12-08
Hi,

I was very excited with my newly installed Ubuntu OS. I spent the last day or so configuring everything & figured it was time to delete Windows. Well, now I have problems:o 

I followed the instructions here:[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

I assumed that I was supposed to boot the disc from the "run ubuntu without affecting my current installation" (or something to that affect) as the tutorial wasn't specific. I followed the remaining simple directions to remove Windows & seemingly deleted the its partition. I was unable however, to resize the Ubuntu partition to use the entire hard drive. I fiddled a bit but always clicked cancel as I wasn't entirely sure how to set the size or even what I was resizing exactly. 

So, I quit "Gparted" & restarted without the disc & received a screen with the following info, amongst other..."No bootable device-insert boot disc and press any key". BUMMER! I inseted the Ubuntu install disc for hoorahs & hit enter but that did nothing so I shut down & rebooted with the disc in & was able to boot from the cd. I chose the last option on the list which was to boot from the first hard disc & I got back into my lovely Ubuntu OS with all of my steup work in tact. 

But now what? I cannot boot without the disc & I also need a hand resizing the partition. I anxiously await your replies :D

---

### Post by sikander3786 on 2009-12-08
I think you messed up your GRUB. You'll have to reinstall it in order to boot from the HDD.

Follow the instructions provided here. You are welcome if any problems exit.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Uadebisi on 2009-12-08
> I think you messed up your GRUB. You'll have to reinstall it in order to boot from the HDD.

Thanks but can you translate that into non-Ubuntu terms please ;) What is a GRUB & how would I have "messed" it up? And I will need to reinstall what exactly? What is HDD?

---

### Post by sikander3786 on 2009-12-08
GRUB is the bootloader for Ubuntu. HDD is a pretty common term, Hard Disk Drive.

When deleting Windows, I think you deleted the MBR which stores bootloader on the Hard Drive.

I think you got it now. Have you checked the link mentioned in my previous post?

---

### Post by Uadebisi on 2009-12-08
I thought that HDD referred to the hard drive but better to be safe than sorry. I do not know what MBR means & yes, I read the tutorial. It might as well be in French..I don't speak that either. 

I don't understand why I had the problem as I followed the directions form the link I listed above. It was rather simple, even for a new Ubuntu user. Is there a simpler explanation of what I need to do because I do not believe I am capable of following that tutorial & I would rather not go back to Windows? Also, I was reading some other threads with similar issues & there was talk of installing " rEFIt". What's that? 

There is still the issue of resizing the partition as well.

**EDIT**- here is a new link at the end of the thread that you supplied sikander...

[http://ubuntuforums.org/showthread.php?p=6391959](http://ubuntuforums.org/showthread.php?p=6391959)

---

### Post by Penguinsunite on 2009-12-08
Hey there, 
    To start off with, the MBR is the master Boot Record which is what microsoft uses to store information on how to boot up and keeps a log of all of the information. I recently switched one of my laptops from fedora to ubuntu and i had the same problem. What I believe the problem is is that when you were switching operating systems, what happened is that during the switch, information from the two operating systems interfered with each other and got corrupted during the deletion. basically windows went down fighting. The way I fixed mine is I used Acronis to wipe all of the information off my hard drive, I mean everything. This way, you dont have to worry about old information screwing up your installation. As far as the resizing issue, when I did the wipe and reinstalled, I did the guided partition using the whol hard drive (its a default option during installation. So wat I would recommend is to get a software program that you can boot from a disc to wipe the entire hard drive and then redo the installation. This is a hassle I know, but it is how I know how to fix the problem. 

Hope this helps!!!
Michael Phillips

---

### Post by sikander3786 on 2009-12-08
Ok. Now follow me.

Boot your Ubuntu install. Go to Terminal. (Terminal is located under Application--->Accessories--->Terminal) and type

```
sudo grub
```

Hit enter and it will prompt for password. Type your password.

Now the prompt will change to grub>

Type

```
find /boot/grub/stage1
```

This will return a location. Assuming it is (hd0,1). Now type

```
root (hd0,1)
```

Now,

```
setup (hd0)
```

And then

```
quit
```

And now remove the CD and restart.

---

### Post by Uadebisi on 2009-12-08
Okay...but before we start...a question about using terminal as I have never used it. When I open a terminal, there is the following info already there...name@computer:~$. Where do I type the info that you are giving me? Do I erase the info already in the terminal first? Also, did you see this link?
[http://ubuntuforums.org/showthread.php?p=6391959](http://ubuntuforums.org/showthread.php?p=6391959)

---

### Post by sikander3786 on 2009-12-08
Yes I have visited the link. That is pretty much complicated.

The default prompt look like name@coumputer. You cannot erase it. You have to just type. It will type in front of that prompt.

---

### Post by Uadebisi on 2009-12-08
> That is pretty much complicated.I just read it & it is almost exactly the same as your instructions??

Also, I am having trouble with the terminal. I typed 
sudo grub & was asked for my password but then it said that it couldn't find it.

Now, I cannot get back to my password prompt. Do I choose clear & reset?

---

### Post by Uadebisi on 2009-12-08
Ps- says "command not found"

---

### Post by sikander3786 on 2009-12-08
Boot from the live cd. Where it says something like Try Ubuntu without making any change to your computer.

---

### Post by Uadebisi on 2009-12-08
sure...I am already in logged into Ubuntu though...you know that right? I just needed to log in with the disc. Also, I was mistaken, the instruction you posted are the same as the instructions for 9.04 which supposedly do not work for 9.10. Instructions for 9.10 are just below the ones for 9.04. 

I will reboot again now  if you like...

---

### Post by sikander3786 on 2009-12-08
Yes you'll have to reboot again.

---

### Post by Uadebisi on 2009-12-08
ok..ready

---

### Post by sikander3786 on 2009-12-08
Sorry I didn't knew if you were using Ubuntu Karmic. You'll have to follow the instructions on the link you provided for Ubuntu 9.10 and later.

---

### Post by Uadebisi on 2009-12-08
Why did you tell me to reboot?

---

### Post by sikander3786 on 2009-12-08
Cause without reboot that couldn't be done either.
Ok now type

sudo fdisk -l

Can you identify the partition on which Ubuntu is installed? And tell me the device boot identifier something like /dev/sda1?

---

### Post by Uadebisi on 2009-12-08
actually, now that I booted with the disc, I checked in Gparted & my drives are   /dev/sda2 /dev/sda5 /dev/sda6  /dev/sda5 is the one with the used space & is indicated in the bar graph next to the unallocated space  DONT FORGET i NEED TO RESIZE THE PARTITION

---

### Post by sikander3786 on 2009-12-08
Ok means ubuntu is install on /dev/sda5

Type

sudo mkdir /media/sda5

Then,

sudo mount /dev/sda5 /media/sda5

And finally,

sudo grub-install --root-directory=/media/sda5 /dev/sda

---

### Post by Uadebisi on 2009-12-08
while booted from the temp install on the disc or do I need to reboot onto my hard drive?

---

### Post by sikander3786 on 2009-12-08
From the live cd.

---

### Post by Uadebisi on 2009-12-08
maybe I am stupid but that makes no sense to me as the the way that I am booted now is not actually into my Ubuntu install???

---

### Post by sikander3786 on 2009-12-08
You will be able to do it either way, from CD or from actual install as the /dev/sda5 mentions the actual installation locations.

---

### Post by Uadebisi on 2009-12-08
forgive me but this is all new to me...  I cannot even get to the second & third lines in the terminal without hitting enter in between...is that right?  I really dont know what I am doing...  getting all kinds of stuff coming up after typing. cleared & reset..i am really sorry but you need to be more specific

---

### Post by sikander3786 on 2009-12-08
Those are two different commands. Hit enter between them. You'll have to do them seperately.

---

### Post by Uadebisi on 2009-12-08
I am making a mess. Should have stayed with windows!  I am lost. When I enter the terminal & type info, a lot of corresponding info appears..is that normal?

---

### Post by Uadebisi on 2009-12-08
Well...I did everything again. So I dont know if doing things twice is bad or not. Not sure if I was supposed to type next to ubuntu@unbuntu or clear & reset first.  So, how do I know if I made a mess?  Shall I close the terminal?

---

### Post by sikander3786 on 2009-12-08
Just follow the commands I posted on the previous page for your ease. Terminal is just like Command Prompt in Windows. You are new to it. No problem. Try to learn everything you are doing.

---

### Post by sikander3786 on 2009-12-08
There is nothing going to be messed up. It is now Windows Buddy. Keep going. You can play a lot with Linux and then get it up running again.

---

### Post by sikander3786 on 2009-12-08
If you have done all the 4 commands, restart your computer without the CD and see if it works.

---

### Post by Uadebisi on 2009-12-08
I fiddled a bit, entered some things more than once, entered commands next to ubuntu@ubuntu then cleared & reset....could I have duplicated the task or is it something that can only be done once?

shall I close the terminal? & now what....resize the partition or reboot?

OOPS... MISSED YOUR POST...I WILL TRY IT. Please read above though

---

### Post by sikander3786 on 2009-12-08
That is normal when you type

sudo fdisk -l

It will show up you hard disk statistics.

---

### Post by sikander3786 on 2009-12-08
Close the terminal and restart and see if it works.

---

### Post by Uadebisi on 2009-12-08
didnt type that...like I mentioned, I got the hard drive info from Gparted.

Here is what I have...

sudo mkdir /media/sda5
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$  sudo mount /dev/sda5 /media/sda5sudo grub-install --root-directory=/media/sda5 /dev/sda
mount: unrecognized option '--root-directory=/media/sda5'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$

---

### Post by Uadebisi on 2009-12-08
nope...didnt work

---

### Post by sikander3786 on 2009-12-08
The problem is that I am not in front of a Ubuntu PC to check that command. Try to boot your actual installation and repeat the commands there. I have to leave now. I'll try to follow you tonight. Bye till then.

---

### Post by Uadebisi on 2009-12-08
thanks & please do check back. I appreciate your help!!

---

### Post by Uadebisi on 2009-12-08
Well, I have very bad news now. I took your suggestion & tried again from the hard drive install. When I entered "sudo mkdir /media/sda5", I was told that it was already installed so I decided to enter the second command "sudo mount /dev/sda5 /media/sda5" & a lot of info appeared. By the way, did all this after clearing the name@computer so that I had a blank terminal.   Then I entered the final command "sudo grub-install --root-directory=/media/sda5 /dev/sda" & some more info came up telling me that it something installed without errors so I thought I did it. But when I rebooted, it didn't work. I got the same message as before about "no bootable device". So, I inserted the cd again as I have always been able to boot from there but now I cannot!!  I received this:  "GNU GRUB version 1.97 beta 4 minimal BASH-likeline editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions."  Now what? This really sucks! I deleted Windows thinking that Ubuntu would be less problematic & so far, I am very wrong. I appreciate all of your help & I hope you can help me fix this.

---

### Post by crimsonshdw on 2009-12-08
I have just read this thread..... When you boot up next, open up your BIOS and make sure that it recognizes your HDD. When I wiped my HDD of windows and installed 9.10 I had a similiar problem. My CD drives were being recognized but not my HDD. I had to reset the jumpers on the motherboard (very simple procedure) and now I have no problems. My HDD is being recognized and it boots fine. :)

---

### Post by talsemgeest on 2009-12-08
Ok, my suggestion would be to boot into the Ubuntu Live CD, and take a look around to try to access your files. If you can, then you can back them up before installing ubuntu onto the whole hard drive. If not, you can have a go at [recovering your files](https://help.ubuntu.com/community/DataRecovery) (warning: it is a slightly advanced link). If you either have your files or have none on the hard drive that you need, you can reinstall ubuntu onto the whole hard drive.

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> 
ubuntu@ubuntu:~$  sudo mount /dev/sda5 /media/sda5sudo grub-install --root-directory=/media/sda5 /dev/sda
mount: unrecognized option '--root-directory=/media/sda5'


Did you manage to solve this? Look what you wrote above, you are typing both commands together. You need to type one, hit Enter and then type the other in the next prompt.

So, boot with the cd and the Try Ubuntu option, open terminal (in Applications-Accessories) and execute the commands:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Do not ask how can it work when you are booted with the cd and not your hdd installation, it works. Just do it if you want grub2 installed on your hdd.

So do the above commands and select Restart after that (from top right, like when shutting down ubuntu), and see if it will boot from the hdd (take the cd out to prevent booting from the cd again).

If that doesn't give you working ubuntu, boot again with the cd and in terminal execute:
sudo fdisk -l

Post the results of that command here.

---

### Post by darkod on 2009-12-08
> **talsemgeest said:**
> Ok, my suggestion would be to boot into the Ubuntu Live CD, and take a look around to try to access your files. If you can, then you can back them up before installing ubuntu onto the whole hard drive. If not, you can have a go at [recovering your files]("https://help.ubuntu.com/community/DataRecovery") (warning: it is a slightly advanced link). If you either have your files or have none on the hard drive that you need, you can reinstall ubuntu onto the whole hard drive.

This is also good suggestion. If you do NOT have any important files on your hdd, just boot with the cd, select Install Ubuntu and at step 4 tell to use the whole disk. BUT ONLY if you don't have important files on it, THE WHOLE DISK WILL BE DELETED!!!

It is much simpler than trying to enlarge the ubuntu partition now, plus it depends in what state it is after all this mess.

---

### Post by Uadebisi on 2009-12-08
:( Uhhhh!

Thank you both...I am still here just needed to sleep finally. Well, I will try the suggestions. What a bummer though. Like I said, I just set all of my preferences...set-up emails, imported all my docs, pictures, etc.

darko,

Your suggestion offers some hope of retaining my install, so I will try it. I know I made a mess. I HAVE NEVER done any of this before so this terminal is all new to me. Am I suppose to first delete the info that appears in the terminal when I open it or do I type next to it? I guess I just needed very detailed instructions to start. For example, after entering one of the commands, I am suppose to hit enter, but this I didn't know. I follow directions well but they need be very pacific ;-). I realize that this may seem basic to you but I have never done it so if there is more that one way to go about this then specific instructions would be greatly appreciated :) As far as entering both commands at once, that is what talsemgeest suggests in his tutorial, that's why I did it that way. Perhaps I misunderstood.

talsemgeest,

I will do what you suggest as well but I don't think that anything of mine is on the cd. Once again, I very much appreciate your help! 

If you go back to the beginning & see the linked tutorial that I followed, I do not understand why this failed to begin with. It was rather simple & I do not believe I did anything wrong...unlike in this thread. Thanks all!! I will be back in a couple of hours. Please check back to see if I am still alive;)

---

### Post by darkod on 2009-12-08
You don't delete anything in terminal. Every line in terminal is starting with info like username@computername. Don' worry about that. You just type the commands as they are. Everything that is written in one line you also type in one line. When the next command is in another line that means you press enter after the previous command and the terminal will take you to the new line automatically which will also start with username@computername.

---

### Post by Uadebisi on 2009-12-08
TY!

Okay...I need to go out for a bit but I tried what you said & the same thing happened as while on the install. When I typed the first command, it says" already mounted or /mnt busy". I look forward to your reply although I may not get back to you for a couple of hours.

---

### Post by Uadebisi on 2009-12-08
ps- believe me, this is very humbling, to appear this stupid in public. however, it's only ignorance & i learn quickly.

---

### Post by Uadebisi on 2009-12-08
Hi all, I am back. Before I try a new install, thus losing all of my info, any comments pertaining to my question in my last post?

> When I typed the first command, it says" already mounted or /mnt busy. 


Thanks!

---

### Post by darkod on 2009-12-08
Well, already mounted means that it is already mounted but that would be strange because when using the LiveCD with Try Ubuntu, the hard disk does not get mounted. Just to make sure we are talking about the correct partition, in terminal type:
sudo fdisk -l

and hit enter. Post the result here.

---

### Post by Uadebisi on 2009-12-08
Well, this is what happened when I ran that command while logged in to Ubuntu on my HD. and when that happened, I did the following, as I mentioned earlier...

"I took your suggestion & tried again from the hard drive install. When I entered "sudo mkdir /media/sda5", I was told that it was already installed so I decided to enter the second command "sudo mount /dev/sda5 /media/sda5" & a lot of info appeared. By the way, did all this after clearing the name@computer so that I had a blank terminal. Then I entered the final command "sudo grub-install --root-directory=/media/sda5 /dev/sda" & some more info came up telling me that it something installed without errors so I thought I did it. But when I rebooted, it didn't work."

Stay tuned for the terminal results of which you requested, but I am pretty sure, ignant as I am;-) that we have the right drive.

---

### Post by Uadebisi on 2009-12-08
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           10314       19457    73449180    5  Extended
/dev/sda5           10314       19086    70469091   83  Linux
/dev/sda6           19087       19457     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by darkod on 2009-12-08
OK, because I don't know why it would say it's mounted, lets try unmounting it first. In termianl run one by one, pressing enter after each:

sudo umount /dev/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Copy the results here.

---

### Post by Uadebisi on 2009-12-08
darko,

I really appreciate this!! This is a big deal! I am also more with it than last night at 4 am when I could no longer  function which exacerbated my frustration. With just a few of your detailed instructions I am already feeling more comfortable with the system. I am not actually as dumb as I sound:)

Here are the next results..

 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           10314       19457    73449180    5  Extended
/dev/sda5           10314       19086    70469091   83  Linux
/dev/sda6           19087       19457     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
ubuntu@ubuntu:~$

---

### Post by darkod on 2009-12-08
Why didn't you continue entering the commands?

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by Uadebisi on 2009-12-08
I am...wasn't sure if you wanted one by one results....here are the results of the next 2 which resulted in seemingly good results. But that's what happened last night too.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           10314       19457    73449180    5  Extended
/dev/sda5           10314       19086    70469091   83  Linux
/dev/sda6           19087       19457     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$

---

### Post by darkod on 2009-12-08
That's good. Now remove the cd and restart, and see if your installation from the hdd will work. :)

---

### Post by Uadebisi on 2009-12-08
ok...just for the sake of learning, why initially did I need to enter 
sudo mkdir /media/sda5 
but not this time? See ya after reboot

---

### Post by Uadebisi on 2009-12-08
Nope! "No bootable device". I have not tried to boot to the hard drive with the cd yet because as you know, that wasn't possible after my work last night

---

### Post by Uadebisi on 2009-12-08
I am able to boot to the HD from the disc again though

---

### Post by darkod on 2009-12-08
Are you sure you haven't removed the HDD option from the BIOS boot options completely? If you want to boot from cd you put CD-ROM before HDD in BIOS, but you do not "delete" HDD completely.
If that was done, now without a cd in the drive, it can't boot from anywhere.
In your BIOS, what are the boot devices specified and in what order?

---

### Post by Uadebisi on 2009-12-08
I do not know what a BIOS is or how to locate the info you are suggesting.

As far as the cd, I am just saying that using it to boot & choosing" boot from 1st hard disc" is the only way for me to access my install on my HD. And, last night after my fiddling with all of this, I was no longer able to access the HD with the cd either, only the temp/Live cd option, the one that doesn't affect a current installation (the first option in the list)

EDIT- Once in to my HD install, I am able to remove the disc & still work

---

### Post by darkod on 2009-12-08
And when you select "boot from 1st hdd" does it load the version of ubuntu on the hdd correctly? If yes, that means it's fine. You have another problem. Very strange. It seems somehow your computer stopped booting from your hdd.
A BIOS is a small software on the mainboard of your computer that runs the initial start process. After you turn your computer on you can usually see some text on the screen, toward the bottom is can say Press Del to enter BIOS, (Delete button), or Press F2, or F12. When you press the button a screen with options will show. That's where you set up from which device to boot first, second, etc.

---

### Post by Uadebisi on 2009-12-08
> And when you select "boot from 1st hdd" does it load the version of ubuntu on the hdd correctly?

Yes sir

---

### Post by Uadebisi on 2009-12-08
I followed these instructions to remove Windows

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)


EDIT- I was reading some other threads with similar issues & there was talk of installing " rEFIt". What's that?

---

### Post by darkod on 2009-12-08
OK, listen. First: Even if we fix this boot problem, and you can boot from your hdd, I have noticed that ubuntu takes barely half of the hdd. Since you decided to remove windows it's best to reinstall ubuntu to the whole hdd to use all of the space. Even if we repair this, half of the hdd will sit unused.

Second: what is getting me worried is that you might have issues with BIOS not wanting to boot from the hdd at all. In this case even after reinstalling ubuntu on the whole hdd it might not boot properly also. But this is not ubuntu's fault, it's BIOS not booting from the drive correctly. As you said yourself, you can successfully boot the hdd trough the cd.

If you do not have some important data in ubuntu on the hdd, I recommend to boot with the cd again, this time select Install Ubuntu, and at step 4 just tell it to use the whole hdd.

After it's installed, remove the cd and restart as asked by the installer. See if it will start successfully from your hdd. If yes, excellent.

If not, you have a problem with BIOS starting up your hdd boot process. We can't sort that out like this, especially since you have no experience changing your BIOS settings. You will need someone's help to come there and help you, some friend that knows computers more for example. That's all we can do.

---

### Post by Uadebisi on 2009-12-08
Well, can't we resize the partition?

I really wish I knew that removing Windows could cause this. There was no mention of it in the tutorial. Obviously, that was in no way directed at you :)

I do not have anyone to assist me with this & cannot pay someone to help so it looks like I may have ruined a perfectly good pc with this install. BUMMER!

If there is no BIOS now, is there a logical reason why there would be upon a full install of Ubuntu?

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> Well, can't we resize the partition?

I really wish I knew that removing Windows could cause this. There was no mention of it in the tutorial. Obviously, that was in no way directed at you :)

I do not have anyone to assist me with this & cannot pay someone to help so it looks like I may have ruined a perfectly good pc with this install. BUMMER!

If there is no BIOS now, is there a logical reason why there would be upon a full install of Ubuntu?

Removing windows shouldn't have done this. It's strange, I can't explain it.
Resizing the partition is possible but new install may help in resolving the problem too, can't be sure. That's why I suggested you do another install if you don't need any data from it. And this time because there is no windows around ubuntu will set itself up slightly different on the drive.

---

### Post by Uadebisi on 2009-12-08
Okay...I just called a friend who works for IBM designing systems. He is a Windows expert with some Linux experience. He said it is definitely not my BIOS. He said & I DO NOT quote, that I need to repair the master boot in Linux & grow the partition. Something about finding the boot strapper in Linux & that because I did a dual boot initially that the sysyem was using Windows to boot but now that it's gone, Linux needs to be set to do this. This is not at all how he explained it though :)

He said that the easiest thing for me to do would be to do a fresh install & that Linux should then handle setting all of this up properly. You seem to be thinking along similar lines. We'll see...

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> Okay...I just called a friend who works for IBM designing systems. He is a Windows expert with some Linux experience. He said it is definitely not my BIOS. He said & I DO NOT quote, that I need to repair the master boot in Linux & grow the partition. Something about finding the boot strapper in Linux & that because I did a dual boot initially that the sysyem was using Windows to boot but now that it's gone, Linux needs to be set to do this. This is not at all how he explained it though :)

He said that the easiest thing for me to do would be to do a fresh install & that Linux should then handle setting all of this up properly. You seem to be thinking along similar lines. We'll see...

I agree with what he said, but the Master Boot Record (MBR) repair for Linux was exactly what we were doing so far. And even after that, you received "no bootable device" error.
That grub-install command does just that, reinstalls grub2 bootloader to your hdd MBR.
It's up to you if you want to reinstall using the whole hdd.

---

### Post by Uadebisi on 2009-12-08
Well Darko,

Why not first try growing the partition via Gparted. Can you walk me thru it as it was a bit confusing? My friend did say it was a 2 part fix which included growing the partition.

---

### Post by darkod on 2009-12-08
Boot from the cd, select Try Ubuntu, and open Gparted (in System-Administration). Then right-click on /dev/sda2 in the list and select Resize. It should show a bar and there should be unallocated space left of /dev/sda2. Drag the left border of /dev/sda2 all the way to the beginning of the bar (that's the beginning of the disk).
Then, within sda2, do the same with sda5. Because it's inside sda2 it needs to be done one by one. That will just schedule the operations. You will see them at the bottom of the Gparted window.
To execute them, click on the big green check mark button in the Gparted toolbar. That will execute the scheduled operations.
If any of the partitions is mounted (has a keys symbol), first unmount it with right-click and unmount (for swap use swapoff).

---

### Post by Uadebisi on 2009-12-08
when right licking on /dev/sda2 there are only options to "manage flags" & "information". The resize option is grayed out

---

### Post by darkod on 2009-12-08
Don't know why. If a partition of any kind exists before it, you have to delete it and it will turn into unallocated space.

---

### Post by Uadebisi on 2009-12-08
I have the option to resize for the sda5

---

### Post by Uadebisi on 2009-12-08
see attachment...what now?

---

### Post by Uadebisi on 2009-12-08
lets try that again

---

### Post by darkod on 2009-12-08
Put delay of 2-3 seconds in the screenshot tool, to make it disappear when taking the shot. Can't see under it.

You see, there is 0 free space before it. You can expand it, just shrink, which you don't want.

/dev/sda2 is like container for both. Unless it's expanded first, you can't do anything with /dev/sda5. I have no idea why the option wouldn't be there for /dev/sda2. Make sure there are no keys symbol for /dev/sda5 and /dev/sda6.

---

### Post by Uadebisi on 2009-12-08
yea sorry...already did a new one

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> yea sorry...already did a new one

Remove the keys from /dev/sda6 with right click, swapoff. That will remove the keys symbol from /dev/sda2 too. That's why resize is greyed out.

---

### Post by Uadebisi on 2009-12-08
> You see, there is 0 free space before it. You can expand it, just shrink, which you don't want.This is why the tutorial confused me...so, now what?

post overlap...will do

---

### Post by Uadebisi on 2009-12-08
It's in process...stay tuned! 

TY for the explanation as this was not clear in the tutorial which is why I couldn't expand sda5. There was no mention of first growing sda2.

Also, you DID tell me that if there were keys that I needed to swapoff. Sorry...didn't follow directions well that time. This may take some time so when it's thru, I suppose I need to reboot to give it a try although I am trying not to have expectations.

If this doesn't work, is it still possible that a fresh install will?

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> 
If this doesn't work, is it still possible that a fresh install will?

Yes, fresh install overwrites everything so it can always work. It deletes all old data.

---

### Post by Uadebisi on 2009-12-08
this will take a half hour at this rate so...stay tuned (as if you have nothing better to do):popcorn:

---

### Post by darkod on 2009-12-08
> **Uadebisi said:**
> this will take a half hour at this rate so...stay tuned (as if you have nothing better to do):popcorn:
It's too late here so I can't stay that long. Don't forget, you can always use fresh install and the Use Whole Disk option.

---

### Post by Uadebisi on 2009-12-08
Well, I cannot thank you enough for your help!! I hope you check back to see how I did. We'll see....

---

### Post by Uadebisi on 2009-12-08
Is anybody still there?

Well, now I have seemingly bigger problems!!!!

Like I said a couple of posts ago, I was resizing the partition & when it was thru I was going to reboot to see if this solved the problem. It did not as I received the same info at start-up "no bootable device...." But I was still able to boot from the cd to my newly formatted HD.

So, I figured it was time to reinstall Ubuntu & lose my existing install & hope that that would enable me to boot up again, as I did prior to removing the Windows partition. But, when I tried to start back up, the machine is stuck on the Gateway screen, with the BIOS Settings <F2> & BOOT menu <F10> at the bottom of the screen. It will not go any further with or w/o the disc & the mahine is running hard. Now what the heck am I suppose to do.

This is really a nightmare!
[B]
UPDATE[/B]- after some time, it moved from the Gateway screen but only back to the "no bootable device" screen. It is no longer booting from the disc!

UPDATE 2- mysteriously, after countless attempts, the system began to boot from the live cd! It is installing now but...we'll see. I am still not sure that this will fix the inability to boot without the disc, which is how this thread started to begin with. At least I think that's how it started :-)

**UPADATE 3-** Now I have yet newer problems. After wiping out my recently installed Ubuntu, I just installed it again on the entire HD. It seemed to install correctly & when I rebooted, it again stuck on the Gateway startup screen for longer that normal then it looked like Ubuntu was going to install, as the logo appeared but that only resulted in the logo disappearing yet the grayish background remained. That's it. That's as far as it went.

Whomever is responsible for writing the installation tutorial should have mentioned that this may result in a nightmare. I have been reading other threads where people are experiencing similar. So, now I do not have Windows or Ubuntu nor does is my machine starting properly. Thank you to all of those who have tried to help me. Your time is greatly appreciated. I am of course open to any other suggestions! I am presently trying to reinstall Ubuntu yet again as the last install didnt seem to take. Also, on start-up, sometimes the machine hangs on the Gateway screen & sometimes it goes quickly to try & load Ubuntu. Which results in a gray screen, which is why I am running the install again.

LAST UPDATE- STILL NO LUCK. Reinstalled, machine stuck on Gateway screen way too long running hard, ubuntu begins to load then...gray screen. So, I installed the disc & w/o rebooting the login appeared & I was able to login to my new install. Obviously there is still something very wrong. Any ideas?

---

### Post by Uadebisi on 2009-12-09
So, here is some info I have received from a friend that may be helpful in diagnosing my problem. 

[COLOR=#1f497d][FONT=Calibri]Growing  the partition won&#8217;t help &#8211; you need a boot record.  I know it&#8217;s not the BIOS  because you can boot successfully from the DVD, and it sees the hdd just fine.   My recommendation is to format the drive and re-install[/FONT][/COLOR]

[COLOR=#1f497d][FONT=Calibri]Next  time it reboots, press F2 to enter the BIOS. You need to set the Boot device  order back to the original settings. When you deleted the previous master boot  record, the BIOS probably automatically re-ordered the devices, placing the hard  disk last, or taking it off the list completely. I&#8217;ve never used a Gateway, but  all BOIS&#8217;s are basically similar. It may be waiting for a network book to time  out before finally moving on to the CD-ROM or HDD (which is why it seems to wait  for a long time and then boot from the CD). I&#8217;d change the order back to be  CD-ROM first, then HDD, then network, USB, or whatever other options are  there.[/FONT][/COLOR]



[COLOR=#1f497d][FONT=Calibri]Not  sure how the Ubuntu installer handles it, but deleting all partitions and doing  a fresh install ***should*** cause the installer to automatically create a,  MBR on the drive. That plus adjusting the BIOS settings should have you back in  business 
[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]That  all looks correct. You could disable the &#8220;Boot to network&#8221; and &#8220;USB Boot&#8221;  options if you wanted things to time-out faster. But the BIOS settings looks  correct to me. ([COLOR=Red]this is in response to my sending him the BIOS settings)[/COLOR][/FONT][/COLOR]
 
 [COLOR=#1f497d][FONT=Calibri]So,  you did a completely fresh Ubuntu easy install? Because it sounds like your HDD  is still messed up.[/FONT][/COLOR]


[COLOR=#1f497d][FONT=Calibri]...the MBR is messed up now. Was there an option to completely wipe the drive and  re-partition during the Ubuntu install?

[/FONT][/COLOR][COLOR=#1f497d][FONT=Calibri]Do  you still have your Windows restore CD? Might be worth trying to put Windows  back on it just to get the hard drive booting again, and proving that there&#8217;s  nothing physically wrong.[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]In  the old days, once Linux altered the boot partition, you had to do a low-level  format to be able to use that drive again with any other operating system other  than Linux. Hopefully that&#8217;s not the case here.[/FONT][/COLOR]

[COLOR=#1F497D][FONT=Calibri]...if you can still boot from the CD and see your HDD, maybe Ubuntu has a drive  wipe utility to completely delete everything?[/FONT][/COLOR]

---

### Post by sikander3786 on 2009-12-09
I thought you would have got your system up running by now Uadebisi. After lots of hard work, I think it was better to reinstall Ubuntu a lot before than now. Have you done it? Most of the people have tried to help you but there is only one hurdle in between "BADLUCK". If you were in my country, I'd have travelled to you and could try to fix your PC. I can't do more than that.

I hope you'll get your PC up again. Have you reinstalled Ubuntu as others mentioned?

---

### Post by Uadebisi on 2009-12-09
Hi sikander,

Yes I have reinstalled, please see my posts above explaining all that I have done.

---

### Post by darkod on 2009-12-09
This is some weird problem and I'm sure somehow your BIOS is involved too. You said sometimes it got stuck at the Gateway screen. That's even before trying to boot the cd or the hdd and has nothing to do with ubuntu or windows.
You also said it say Boot menu F10. If you press F10 and open the boot menu and you select the hdd, does the error still happen.
It seems you have correctly installed ubuntu on the hdd but out of whatever reason your BIOS is not booting the hdd.
Try the F10 and select hdd, see what happens.

---

### Post by Uadebisi on 2009-12-09
Hi Darko,

I will try shortly. Stay tuned. Am on the phone w/ a Linux expert who is trying to help. Pleeeease stay with me if you can.

---

### Post by Uadebisi on 2009-12-09
You ready for this Darko?

So, after resetting to the default BIOS, when I booted, the machine again hung on the Gateway splash screen & when it finally moved on to the Ubuntu load screen, it again stuck on the gray screen. So, we rebooted & hit F2 to enter the BIOS again but the keyboard was dead! 

So, we booted again, waited for Gateway splash screen to go thru to the Ubuntu gray screen & hit ctrl alt F2. Here we learned that there was a 110 error related to the USB bus. I was advised to unplug the printer, which is connected via USB & to reboot. Well....I had a quick & normal boot into the Ubuntu login screen!!!

We tried booting with the printer plugged into the USB ports on the front of the machine but the result was the same. So, either there is one USB bus  for both front & back & it is bad or it is something else pertaining to the printer. I will try some basic diagnosing (unplugging, new cable, uninstall-reinstall, etc)

Any suggestions?

---

### Post by darkod on 2009-12-09
No suggestions about the printer but it seems the ubuntu works fine with the printer unplugged. :)

---

### Post by Uadebisi on 2009-12-09
okay then, but the printer worked just fine with Windows installed.

Well, I am going to uninstall & reinstall the printer via Linux, as compared to how it was done originally thru Windows. 

**edit-** From what I am reading, there is not an option to install my printer using the HP cd.

edit 2- installed again, the Linux way, but the printer no longer works as it once did. It was detected & installed but it will not print a test page??? 

I also tried printing something else & the printer queue icon appeared next to the speaker. The print job was listed, did not print, then disappeared.

EDIT 3- I have some good news. After reloading the printer & restarting, I did not get stuck at the Gateway splash screen. I went quickly to the login. However, I still can't print. The machine revs up, then nothing.

Now I cannot get certain info from the help menu...just stays loading! This is really a nightmare...

---

### Post by Uadebisi on 2009-12-09
Darko,

You still there buddy?

Listen, I opened another thread specifically for the printer issues just in case I lost you :) & because my initial problem posted here has been fixed....so far.

[http://ubuntuforums.org/showthread.php?p=8472239](http://ubuntuforums.org/showthread.php?p=8472239)

I can print now too! Read this from the other thread...

"As I am still trying to diagnose the problems, I decided to plug my printer into my old Windows machine, that also has the HP printer installed. Just wanted to make sure the printer & usb cables were okay, & they worked fine. So, I plugged the printer back into my machine with Ubuntu installed & just for hoorahs, I tried to print a test page again. Guess what....it printed!!!

Can someone please explain what the heck is going on here? My last two remaining problems seem fixed (the machine boots into Ububtu even with the printer installed & it prints). But considering all of the problems I have had and that there are still a couple of unanswered questions as to why the last couple of problems are now seemingly fixed, I am wondering what's next?

---

