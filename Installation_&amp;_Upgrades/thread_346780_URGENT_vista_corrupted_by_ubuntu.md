---
title: "URGENT: vista corrupted by ubuntu?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by quickuser on 2007-01-26
All of a sudden Vista is not booting up past the logo screen (with the green animated progress bar). Actually, it goes into blank screen mode after 1-2 minutes and nothing happens ever after that.

Worst yet, even the Vista Ultimate CD (which I used originally to install, twice before) is NOT loading past the same screen (logo)! it first goes through the 'loading windows files...' then boots to the logo screen and nothing happens for several minutes!

I also tried booting in safe mode, it goes through the scrolling of loading files and always gets stuck on crcdisk.sys file

Originally before all this I simply booted (not installed) from Ubuntu CD to test it out. I attempted to install and was stuck on step 5/6 where it asks for partition. I made it 40GB (120GB total drive) and nothing was happening, I successfully canceled and then all broke loose after that.

What should I do? I'm really stuck, can't boot of Vista CD nor drive. I have critical data on my hard drive.

Vista RTM Ultimate
SONY VGN-FE-770G

dxdiag info

------------------
System Information
------------------
Operating System: Windows Vista™ Ultimate (6.0, Build 6000) (6000.vista_rtm.061101-2205)
System Manufacturer: Sony Corporation
System Model: VGN-FE770G
BIOS: Phoenix NoteBIOS 4.0 Release 6.1
Processor: Intel® Core™2 CPU T5600 @ 1.83GHz (2 CPUs), ~1.8GHz
Memory: 2038MB RAM
Page File: 1181MB used, 3114MB available
Windows Dir: C:\Windows
DirectX Version: DirectX 10
DX Setup Parameters: Not found
DxDiag Version: 6.00.6000.16386 32bit Unicode

---

### Post by Jussi Kukkonen on 2007-01-26
> Worst yet, even the Vista Ultimate CD (which I used originally to install, twice before) is NOT loading past the same screen (logo)! it first goes through the 'loading windows files...' then boots to the logo screen and nothing happens for several minutes!

Doesn't this pretty clearly imply that this is not related to anything on the hard disk? The only thing I can think of is a hardware problem -- it does sound far fetched that  a motherboard or something would break exactly when you're trying out a new OS, but I don't think those symptoms are explainable by anything else.

EDIT: you could try the memory check on the ubuntu livecd.

---

### Post by jhaitas on 2007-01-26
sounds like a blessing to me

---

### Post by quickuser on 2007-01-26
> **jhaitas said:**
> sounds like a blessing to me

I'm not here to listen to your opinion about vista so find something else to do with your time.


Jussi: I already ran memory check from the cd, all passed

---

### Post by peachy on 2007-01-26
Hi, can you still boot into the Ubuntu live CD?

If you can I would do so and try and copy some of your data across to a usb key.

---

### Post by jhaitas on 2007-01-26
try contacting microsoft's legendary tech support

---

### Post by quickuser on 2007-01-26
> **peachy said:**
> Hi, can you still boot into the Ubuntu live CD?

If you can I would do so and try and copy some of your data across to a usb key.

how? I went to the partition manager and it would not let me open the windows partition, some error about no permissions. 

Any workaround?

---

### Post by cblanquer on 2007-01-26
If I understood well you tried to get a 40 Gb partition from your 120 Gb disk. 

Did you pick your gigas directly from the existing Windows partition. If affirmative, this might be a reason of failure for WV.:( 
(If instead you had a free partition that you then used for U, then it might be a problem related to WV not liking to share with different OS, as read in several forums/sites. )

Supposing the first case, you took a part of your WV partition to release it and assign it to U, you have a problem that WV will not solve by itself.
Up till my technical knowledge there (so maybe other have better advice and depending what data you do want to recover) you should:
[LIST]
[*]either terminating installing Ubuntu, use it to access to the WV partition and save the data to an external hard disk
[*]either installing any OS on a different hard disk (if available), boot from it and again copy the data from the original WV partition to another place
[/LIST]

Recently my main hd started dying in the Windows partition so I had to do a similar operation - by chance I am running 2 HDs so I simply got an RMA for the faulty one and did the operations on the 2nd one:
[LIST=1]
[*]save all the data, 
[*]repartition the disk, 
[*]reinstall W
[*]reinstall U
[*]copy data back there
[*]recustomise each of the OS
[/LIST]

In both cases, before performing any of those actions, googelise a little to understand how can WV run on a PC with other OS, also wait for more opinions on your problem and overall keep coldblooded before acting. I would recommend also to take short notes of any action to track any possible mistake.
Good luck.

---

### Post by quickuser on 2007-01-26
Let me clarify that:

This is a Sony laption. One hard drive, I also have a 2GB usb.

please read my last post about permission problems

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> how? I went to the partition manager and it would not let me open the windows partition, some error about no permissions. 

Any workaround?
So I assume the live CD still boots ok?

Does it find and mount your windows partition somewhere in /media?

Please give us the exact steps you are taking and the exact error messages.

Please also open up a terminal and give us the output of the following:
If you have SATA disks:
sudo fdisk -l /dev/sda

or IDE:
sudo fdisk -l /dev/hda

---

### Post by foob on 2007-01-26
This is a guess but....

I installed ubuntu 6:10 on a Windows Media Center Edition 2005 XP system and used the resize tool when partitioning. It worked but a lot of strange things were happening with XP including some drivers not working properly. I think this is because Windows does a poor job of defragmentation where placement is concerned. When working with Windows, My advice would be to not use the resize tool.

---

### Post by EvilMarshmallow on 2007-01-26
Wow, jhaitas, did MS run over your dog or something?

I don't like 'em, I switched to Ubuntu as well for the same reasons, but MS Bashing won't solve the problem.

Quickuser: Definitely start by trying to boot Ubuntu from the LiveCD and recover what data you can.

Do you have access to an XP CD?  You could try to install an older version and see if it does the same thing... if it does then I agree with Jussi, it's hardware related.  Could be a bad section on the hard drive in a "lucky" spot, could even be a power supply about to go bad.  I've seen those do some *really* weird crap when they're about to die.

---

### Post by peachy on 2007-01-26
> **EvilMarshmallow said:**
> Wow, jhaitas, did MS run over your dog or something?

I don't like 'em, I switched to Ubuntu as well for the same reasons, but MS Bashing won't solve the problem.

Quickuser: Definitely start by trying to boot Ubuntu from the LiveCD and recover what data you can.

Do you have access to an XP CD?  You could try to install an older version and see if it does the same thing... if it does then I agree with Jussi, it's hardware related.  Could be a bad section on the hard drive in a "lucky" spot, could even be a power supply about to go bad.  I've seen those do some *really* weird crap when they're about to die.
Maybe the Vista CD is freaking out when it goes through the "check to see if any other MS OS's are installed" bit and that's why it's hanging

just a thought....

EDIT: I meant when it checks to see if Vista is already installed

---

### Post by cblanquer on 2007-01-26
My questions: did you have an initial big partition where you extracted the 40 Gb ?

My proposals assuming this is what happened: 
[LIST]
[*]terminate installing Ubuntu (it is not clear you are trying to do this, are you? have you tried agan after rebooting and choosing the manual set up of partitions)
[*]if actually you are trying and that does not work, a possibility is to download a gparted SIO image, burn it to a CD and boot form it, create tha partitions and try reinstalling Ubuntu, but this seems unnecessary to me, you should be able to create the partitions at Ubuntu installation over the 40 Gb you took from the big thing, then copy the data
[*]other idea: CD-boot a Knoppix OS and try to copy the data you want to keep into an external drive - possible you need to buy it, it depends how valuable are the data to you
[/LIST]
Never operate on the remaining WV partition if you want to save your data. You could write over them.

---

### Post by wthanna on 2007-01-26
There is a good chance your Windows partition is corrupted.  Did you defragment before trying to "shrink" an existing partition? Did you backup the partition before attempting to change it? This advice may be a little late for your situation, but resizing a partition with data on it is ALWAYS a dangerous situation.  This is not the fault of Ubuntu.  You need to be aware of this with any partition tool and operating system.  Hopefully you will be able to recover your data using a live CD. You will probably need to reinstall Vista and Ubuntu.  If you do, be sure to do all of your partitioning BEFORE installing your operating systems if at all possible.  This is really the only safe way to do it. It's always a bit risky taking space away from an existing partition that contains data.

---

### Post by quickuser on 2007-01-26
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  12  Compaq diagnostics
/dev/sda2   *         915       14593   109876567+   7  HPFS/NTFS

```

/dev/sda2 shows access path of /tmp/disk-conf-sda2
/dev/sda1 shows 'none' access path and 7gb partition

both are windows ntfs file systems

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  12  Compaq diagnostics
/dev/sda2   *         915       14593   109876567+   7  HPFS/NTFS

```
Ok, it *appears* Ubuntu hasn't changed you partition table at all.

Can you see any data in the folder /media/sda2? If so Ubuntu has mounted you windows drive and you should be able to recover the data. If not you can try manually mounting it.

Why do you have a Compaq diagnostics partition on a Sony?

---

### Post by quickuser on 2007-01-26
> **peachy said:**
> Ok, it *appears* Ubuntu hasn't changed you partition table at all.

Can you see any data in the folder /media/sda2? If so Ubuntu has mounted you windows drive and you should be able to recover the data. If not you can try manually mounting it.

Why do you have a Compaq diagnostics partition on a Sony?

I opened up computer and went to media folder, it is empty

What do I do from here?

---

### Post by quickuser on 2007-01-26
Also, the /tmp/disks-conf-sda2 folder has a lock icon on it.

when attempting to browse it, error: 

The folder contents cannot be displayed....you do not have necessary permissions to view th content of /tmp/disks-conf-sda2

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> I opened up computer and went to media folder, it is empty

What do I do from here?
create a folder called "windows" in /media either through the GUI or at the command line:
mkdir /media/windows

then at the command line:
sudo  mount /dev/sda2 /media/windows -t ntfs -r

EDIT: I'm assuming the liveCD supports NTFS, i can't remember...

---

### Post by quickuser on 2007-01-26
I tried creating folder via terminal and it says permission denied

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> I tried creating folder via terminal and it says permission denied
sorry,

sudo mkdir /media/windows

---

### Post by quickuser on 2007-01-26
I ran sudo mount /dev/sda2/media/windows -t ntfs -r 

but it gave me "usage...." list of how to use this command?

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> I ran sudo mount /dev/sda2/media/windows -t ntfs -r 

but it gave me "usage...." list of how to use this command?
sudo mount /dev/sda2 /media/windows -t ntfs -r 

note the space between /dev/sda2 and /media/windows

sudo (run as root) mount (mount something) /dev/sda2 (device, second partition on first serial disk)  /media/windows (mount point) -t ntfs (file system type ntfs) -r (read only)

---

### Post by quickuser on 2007-01-26
Thanks. Ok I ran that. What should I do now? I tried to access /media/windows again
and it still gives me permission error

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> Thanks. Ok I ran that. What should I do now? I tried to access /media/windows again
and it still gives me permission error
what error, it may be because you created the dir as root, my mistake

do:
ls /media/windows

if there is any error do: 
sudo ls /media/windows

---

### Post by quickuser on 2007-01-26
I checked properties of /media/windows folder and it shows owner/group as "root"

sudo ls /media/windows show my files :)

Now its a matter of transferring them to my 2gb usb

Another odd problem is, I was taking screenshots and saved them to the usb (200mb free), but when I plug the usb in the other laptop (one using now to type here), the file do not show up. I waited at least 15 seconds or so before unplugging the usb. Even more odd, it shows 2 ubuntu files I copied earlier and deleted at least 5 times now, why is that?

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> I checked properties of /media/windows folder and it shows owner/group as "root"

sudo ls /media/windows show my files :)

Now its a matter of transferring them to my 2gb usb

Another odd problem is, I was taking screenshots and saved them to the usb (200mb free), but when I plug the usb in the other laptop (one using now to type here), the file do not show up. I waited at least 15 seconds or so before unplugging the usb. Even more odd, it shows 2 ubuntu files I copied earlier and deleted at least 5 times now, why is that?
ok great, my mistake, ntfs mounts as read only to root by default. 

The UBS key should automount in /media when you add it.

you need to unmount /media/windows then remount with permissions for your user so at the terminal type:
```
id
```
you will get something back like this: uid=1000(user) gid=1000(user) groups=4(adm) etc etc
note the uid and gid values.
then at the terminal type
```
sudo umount /media/windows
```
then type
```
sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=1000,gid=1000,umask=444
```
but change the uid and gid numbers you got from the output of "id"

hopefully you will now be able to access you files via the gui

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> I checked properties of /media/windows folder and it shows owner/group as "root"

sudo ls /media/windows show my files :)

Now its a matter of transferring them to my 2gb usb

Another odd problem is, I was taking screenshots and saved them to the usb (200mb free), but when I plug the usb in the other laptop (one using now to type here), the file do not show up. I waited at least 15 seconds or so before unplugging the usb. Even more odd, it shows 2 ubuntu files I copied earlier and deleted at least 5 times now, why is that?
I don't know the answer to that but have seen it before, maybe a search on the forums might reveal the answer or maybe somebody reading this can help us?

---

### Post by quickuser on 2007-01-26
I unmounted and then ran

sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=999,gid=999,umask=444
(no error message)

However, still getting permission denied when attempting to access /media/windows folder via computers

I even tried this and got "read only filesystem" error

sudo touch /media/windows/test.txt

---

### Post by peachy on 2007-01-26
ok, that's odd, i've not mounted ntfs before so i'm learning too.

Let's
```
sudo umount /media/windows
```
then type
```
sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=1000,gid=1000,umask=777
```
but change the uid and gid numbers you got from the output of "id" as before

Edit: so type:
```
sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=999,gid=999,umask=777
```

---

### Post by quickuser on 2007-01-26
Still getting permisison errors

---

### Post by peachy on 2007-01-26
> **quickuser said:**
> Still getting permisison errors
```
ls -lrt /media/
```

---

### Post by jhaitas on 2007-01-26
has microsoft made any modifications to ntfs for vista? i recall that they modified ntfs when migrating from windows 2000 to windows XP... if they have, in fact, modified ntfs this could be the root of the problem... i do know that they are taking drm very seriously in vista (some may say they are taking it too far) - that is neither here nor there... i wouldn't rule out the possibility that they have attempted to lock out access to data from all other operating systems...

this of course is temporary seeing as the open source community will hack this "feature" in no time... in the mean time you might want to file a bug report to bring this to the attention of the developers... we do, after all, need the capability of reading vista's file system if we are to undermine it ;-)

---

### Post by peachy on 2007-01-26
> **jhaitas said:**
> has microsoft made any modifications to ntfs for vista? i recall that they modified ntfs when migrating from windows 2000 to windows XP... if they have, in fact, modified ntfs this could be the root of the problem... i do know that they are taking drm very seriously in vista (some may say they are taking it too far) - that is neither here nor there... i wouldn't rule out the possibility that they have attempted to lock out access to data from all other operating systems...

this of course is temporary seeing as the open source community will hack this "feature" in no time... in the mean time you might want to file a bug report to bring this to the attention of the developers... we do, after all, need the capability of reading vista's file system if we are to undermine it ;-)
that's a good point, but we can read this as root so i assume it's a linux permission problem?

Is anybody able to give the answer to what we've done wrong?

---

### Post by quickuser on 2007-01-26
ls -lrt /media


shows that windows folder is group/owner of 'root' and dr-w----- permissions

---

### Post by quickuser on 2007-01-26
Someone please help :(  This is a nightmare

---

### Post by John.Michael.Kane on 2007-01-26
These may be of use..
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Fstab guide:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

How to Dual Boot Vista and Linux:
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)
[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

---

### Post by quickuser on 2007-01-26
I don' think that will work when running live from boot cd (ubuntu)

Please explain

I've already mounted as /media/windows


my /etc/fstab only shows this:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by geek_Man on 2007-01-26
Don't know if this will work, but go into the terminal and type "sudo nautilus". Don't do gksudo 'cause I don't know what permissions you'll get. Then try doing whatever you're trying to do.

---

### Post by quickuser on 2007-01-26
I really need help folks, please

I tried sudo nautilis, bad command line?

---

### Post by quickuser on 2007-01-26
I restarted again in live boot mode of course and now when I go to computer I see the 104.8GB volume drive. (wasn't there before), this is the Windows partition

When I try to open it I get an error

unable to mount the selected volume
error: device /dev/sda2 is not removable
error: could not execute pmount

So I ran sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=999,gid=999,umask=444
and now I get "you do not have the permissions necessary to view the contents of 'windows'

What should I do?

---

### Post by quickuser on 2007-01-26
What about a boot recovery cd?

I tried Active@ and it detected the drivers, shown th files
and detected my usb drive but it would not allow me to copy
to the usb as it is 'fat32' or such.

I'm trying ubcd4win now as well.

Any suggestions?

---

### Post by geek_Man on 2007-01-26
It's Nautilus (with a "u"), but I'm sure it was just a typo in your post. Other than that I don't know how to help.

---

### Post by peachy on 2007-01-27
> **quickuser said:**
> I restarted again in live boot mode of course and now when I go to computer I see the 104.8GB volume drive. (wasn't there before), this is the Windows partition

When I try to open it I get an error

unable to mount the selected volume
error: device /dev/sda2 is not removable
error: could not execute pmount

So I ran sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=999,gid=999,umask=444
and now I get "you do not have the permissions necessary to view the contents of 'windows'

What should I do?
Hi, when you restart you need to redo all the steps we went through before.

let's look at the partition table again
```
sudo fdisk -l /dev/sda
```

running Nautilus as root is the solution, hadn't thought of that.

---

### Post by pvilleSE on 2007-01-28
Hope I can help some, I went through the opposite nightmare today, I had to go through all kind of loops to get vista installed when I already had Ubuntu, but that is another topic, but I think I learned somethings that might help you.

First off deleted files on usb keys sometimes still show up later bc sometimes they go into a trash can for the usb key and the trash bin icon does not look like anything is in it but the files on your removable media are, you have to open the trash can and then click to empty it in the menu.

Also if you want a graphical nautilus as root, you do want to do gksudo nautilus, that gives you root permissions in a graphical sense, maybe that will fix your permission problems.

If not a solution I used when my sister toasted her windows partition was I downloaded a program call the [Trinity Rescue Disk]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"), it is a small Linux distro specifically designed for salvaging files.  Basically you boot the disk then type a 1 to start normal mode, then you get to a command line you type "mountallfs" that mounts all harddrives and usb drives.  Then you use the ["cp" command]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cp") to copy the files you want.  

In some of my research I was heavily warned not to resize the Vista partition, that it would be messed up.

Hope that helps.  I will try to check back to see if I can help more.

---

### Post by dahopp on 2007-02-07
I believe I experienced the same issue you did.  I booted off an Ubuntu Cd, and successfully resized my Vista partition and completed the install.  Then I restarted and vista would not boot, nor could I boot off my vista dvd. Booting into safe mode would hang at crcdisk.sys.
I found my solution here <http://opensource.apress.com/article/163/taking-a-look-at-vista-part-iii>

He said run checkdisk. So I booted off a Windows 2000 Cd (an XP disk ought to work also, or your other favorite boot disk that plays nice with ntfs), chose repair, then recovery console (command prompt). Navigate to c:\windows\system32, then run chkdsk /r.  I then restarted my machine and booted into Vista no problem.  Hope you get your problem resolved.

---

### Post by jhaitas on 2007-02-07
perhaps ubuntu should put a warning up about resizing vista partitions until this problem is resolved.

---

### Post by JugglesGeese on 2007-02-10
I'm having exactly the same problem, but I think I've found a workaround.

I decided that I wanted to dual boot my desktop with vista ultimate and ubuntu 6.1.  I had already successfully done a dual-boot scenario on my laptop by running partition magic 8 under XP, then installing vista, and then booting the live cd and running the ubuntu installer.  Grub picked up my windows partition, as it should, and all was well.

The difference between my laptop and desktop install was that with my desktop, I already had vista installed.  Since partition magic doesn't run under vista, I booted the live cd and ran gparted  Then, before installing ubuntu, I wanted to test to make sure I could still get into windows.  I got to the same point...couldn't get past the splash screen, couldn't boot the vista cd, safe mode stopped at crcdisk.sys.

I read an article that said that MS completely changed the boot process for vista, and to get around this problem you can run chkdsk on your sys partition and it should boot.  Ahh...but therein lies the caveat.  How do you get to a command prompt to do the chkdsk?  We already know the vista cd won't work, and a FAT boot floppy won't work because it can't read the ntfs partition.

After reading that, I attempted to boot to my old XP install disk to attempt to run the good old XP recovery console, hoping that it would run for a vista install.  No such luck (I got stuck when it prompted me for the admin password).  But lo and behold, I then tried re-running the vista setup cd after that, and it let me in.  I ran chkdsk on the drive, and I was able to get back in.

So, to sum up:

[LIST]
[*]Boot to the live cd
[*]Perform the resize operation using gparted
[*]Reboot to the XP install cd
[*]Go to the recovery console
[*]Reboot to the Vista Install CD
[*]Choose the Repair Option
[*]DO NOT opt to have windows automatically fix the boot problem if it prompts you
[*]Go to the command prompt, switch to the c: drive and run chkdsk with no options
[*]Reboot
[*]Enjoy a nice drink of tequila *
[/LIST]

Anyway...hope this helps :cool: 

* (or other beverage of choice)

---

### Post by isenalim on 2007-02-15
Hi,
quickuser did you manage to recover your files and run again Vista?

In order to solve all of your problems with permissions, there is a very simple workaround. Just type

sudo gnome-terminal

and you will get a new window open with all root priviliges.

I am now in the same troubles you were a couple of weeks ago. I have a very similar laptop, Vaio fe41m, and after resizing the Vista partition with ubuntu I just got blank screen after the first few seconds in which Vista seems to start. Sama behaviour with and without Sony rescue CD's

I have tried accessing the filesystem with an XP installation disk in order to run chkdsk but it asks me for the Administrator password, that is not the one I set up for the only user there was in Vista and I have no idea of what it could be.

If I try to manipulate again the Vista partition with Ubuntu or even with System rescue CD, which has a more recent version of ntfsresiize, I get an error saying that there are problems in the ntfs journal.

I am tempted to simply delete the Vista partition and see if the Sony Rescue CDs are able to reinstall Vista but I am afraid f what could happen if it doesn't work...

Please, let me know how you solved the problem!
Thanks a lot!

---

### Post by lamalex on 2007-02-15
knoppix dude. recover your data, then start messing around.

---

### Post by isenalim on 2007-02-16
Thanks,
no problem with data, I can recover them even with the ubuntu live cd.
The problem is now: how do I recover Vista? Is there any linux utility that can fix the vista journal?
Otherwise I will wipe the partiotion insert the recovery cd and cross my fingers.

Anyway, it would be highly desirable that Feisty deals correctly with Vista partitions, because the Vista partition editor is really bad and doesn't let you shrink your partition as much as you would (in my case, minimum size was 77 G, for a 110G partition!)

Bye

---

### Post by Stealth on 2007-02-16
I had the same thing happen. Vista installed, then Ubuntu, but I resized its partition and Vista (nor the CD) would boot. I was just finished reformatting my laptop, so I had no special data, but I had to reformat once more and start again, this time, no resizing. :P

Vista has changed some of things in NTFS and that's what I assume is the problem.

---

### Post by isenalim on 2007-02-16
Hi there,
I post my solution, found by the Sony telephone customer care.

During the Sony logo press F2 to enter the BIOS. Press F9 to load default settings and then F10 to save and exit. As for magic, Vista started the recovery utility, corrected the errors in the filesystem and finally reboot in its shrunk filesystem.

At this point my filesystem was 50G (as I had asked for to Gparted) but the partition was still 110G. Anyway the system was very slow and I decided to use the Vaio recovery DVD's I had created before messing around everything. 

Booting from the first DVD I chose Vaio Recovery Utility. This is very beautiful and useful. It allowed me to chose how to partition the hard drive and finally start the recovery. At the moment a fresh new installation of Vista is being performed on my laptop, I will report on how to install Ubuntu after that.

Is the nightmare over?

---

### Post by vincentvee on 2007-02-22
> **isenalim said:**
> Hi,
quickuser did you manage to recover your files and run again Vista?

In order to solve all of your problems with permissions, there is a very simple workaround. Just type

sudo gnome-terminal

and you will get a new window open with all root priviliges.

I am now in the same troubles you were a couple of weeks ago. I have a very similar laptop, Vaio fe41m, and after resizing the Vista partition with ubuntu I just got blank screen after the first few seconds in which Vista seems to start. Sama behaviour with and without Sony rescue CD's

I have tried accessing the filesystem with an XP installation disk in order to run chkdsk but it asks me for the Administrator password, that is not the one I set up for the only user there was in Vista and I have no idea of what it could be.

If I try to manipulate again the Vista partition with Ubuntu or even with System rescue CD, which has a more recent version of ntfsresiize, I get an error saying that there are problems in the ntfs journal.

I am tempted to simply delete the Vista partition and see if the Sony Rescue CDs are able to reinstall Vista but I am afraid f what could happen if it doesn't work...

Please, let me know how you solved the problem!
Thanks a lot!

you know, if you reformat and then run the rescue cd, everuthing should work out fine.....no guarantee tho
but then how do you get ubuntu up on the same drive??
i think that is gonna be a problem with windows from here in, MS doesn't like dual booters, never have and i think they have worked in a fix to stop it happening

---

### Post by isenalim on 2007-02-24
Hi,
it is still possible to dual boot without any problem. The only problem was that the installer on Edgy does not support resizing Vista partition. It is enough to resize the Vista partition with the utility provided by Vista itself and then run the installer.

The installation went perfectly and Ubuntu recognized correctly I had Vista and put the entry in Grub.

Everything perfect! No worries, Vista is not a danger for Linux but a great oppotunity, in the sense that everybody that will not like to upgrade its system and want to have the new Vista features (and much more) will have to go to Linux!

---

### Post by JimRetired on 2007-03-07
Had the same problem but I had all my data already backup. What fixed it for me was use the partition manger and reformat /dev/sdb1 back to ntfs then reboot and I had have Vista back running just fine. Hope they find a way to dual boot with Vista.

---

### Post by louieb on 2007-03-07
> **quickuser said:**
> how? I went to the partition manager and it would not let me open the windows partition, some error about no permissions. Any workaround?
Ubuntu Live CD is not the best for copying  data off a hard drive. It can be done but its a pain.  Get the Knoppix or Puppy Live CD if you can. IMHO Two of the best Live CDs out there.

---

### Post by mooseydoom on 2007-03-17
> **dahopp said:**
> I believe I experienced the same issue you did.  I booted off an Ubuntu Cd, and successfully resized my Vista partition and completed the install.  Then I restarted and vista would not boot, nor could I boot off my vista dvd. Booting into safe mode would hang at crcdisk.sys.
I found my solution here <http://opensource.apress.com/article/163/taking-a-look-at-vista-part-iii>

He said run checkdisk. So I booted off a Windows 2000 Cd (an XP disk ought to work also, or your other favorite boot disk that plays nice with ntfs), chose repair, then recovery console (command prompt). Navigate to c:\windows\system32, then run chkdsk /r.  I then restarted my machine and booted into Vista no problem.  Hope you get your problem resolved.

Thanks a lot for this tip! I was having the same problem, where Vista got stuck at crcdisk.sys in safe mode.  After running chkdsk, I used grub to boot off the sony hidden partition and restore the c drive.

---

### Post by helsley on 2007-03-18
> **mooseydoom said:**
> Thanks a lot for this tip! I was having the same problem, where Vista got stuck at crcdisk.sys in safe mode.  After running chkdsk, I used grub to boot off the sony hidden partition and restore the c drive.

I had the exact same issue as the OP, but don't have any older windows discs kicking around to run chkdsk from.  A bit more work, but another alternative (which ultimately worked) is using ntfsfix from ubuntu, which will sufficiently repair the Vista partition to a point where at least the Vista install cd will boot properly so the repair utility can be used.

---

### Post by nick122147 on 2007-05-13
same problem here. ntfsfix worked for me. very straightforward and quick. then windows will fix the rest itself (no need for vista dvd)

---

### Post by Ric95 on 2007-05-13
I had a similar problem the first time I set up dual boot. It turned out the partitioner I used set the Windows ntfs partition with the 'hidden' property on. 
A good first thing to try is to boot up with a partitioning tool( partition magic or sfdisk, mabey the ubuntu installer?) and make sure it's not hidden.

---

### Post by jerrylamos on 2007-05-13
We can't quite tell what the situation was before you started.

Did Vista have all 120 gb in its partition?  If it did, then it is likely to have files scattered all over the 120 gb.  If you remove some of Vista's partition it could have lost programs and data it needs to run.  Note Microsoft products expect to be the first partition on the first hard drive.

How you have to free up space for linux is to defrag Vista.  After it finishes, look in Details and see how many gb are left clear at the top with absolutely nothing in them.  In my case with XP there were a couple big fat files up there which turned out to be the paging files.  So I went into control panel, system, ... virtual memory and turned off paging, defragged again, and then saw how much space I could safely remove from XP.

Then in Gparted partition editor I resized XP down only as much as I was sure XP wasn't using at the top.  With that free space I could then make a Linux swap and a Linux / partition.  You can do a lot with Linux with 20 gb; you can do some running with 4 gb.

There is an alternative method of installing Ubuntu without doing any repartitioning.  It's called Wubi [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
I haven't tried it.  Some people run on it, some have problems.  I think it is just for XP so far, with Vista in the works.

In essence, with XP (soon Vista) you install a program which allocates a large XP file and then Ubuntu gets installed in that file.  When you boot XP you have a choice of running XP or Ubuntu.

Jerry

---

