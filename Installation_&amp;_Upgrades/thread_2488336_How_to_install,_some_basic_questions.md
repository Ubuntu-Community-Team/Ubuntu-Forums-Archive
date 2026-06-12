---
title: "How to install, some basic questions"
date: 2023-07-02
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2023-07-02
Ok, I was able to install *ubuntu by myself in the past, but things may have changed since then. 
 Now linux computers I was using until recently are down, for different reasons.  
Now have a windows computer and a new computer.  Want to install kubuntu on the new one. //   

So WHAT TO DO NOW: //

    1. I will go to the official ubuntu site, and choose one insallation, and download it, 
and then what BURN IT to a flash disk?  how?  // 

  2. Can I trust windows for it? I mean, the file will be downloaded via firefox on a windows computer, which is not opensource.  
Then how do I locate the file and what do I do with it? How do I check HASH ? 
 I don't even see a command prompt here. //   

3. Do I plug in flash disk into the new computer?  How do I make the computer ready to read the flash disk.
 I mean, do I go to BIOS and other places?  Use one of  f1, f2, f8, f10, f11, and modify settings?   
Can installing linux be impossible? // 

  4.  More detail: Do I need to enable/disable some inside BIOS and other pages under Fx 's (x a number a above).
  Why so many pages like f2, f8,...all with different settings, not sure what the connection between them is. 
Once I install the ubuntu, do I need to bring those settings back ? 
 Of course I want to erase everything completely, and format with linux. //

   5. Last time I installed ubuntu, I was asked encryption PW twice. 
 I mean, different PW's, none being user admin pw's, with slightly different names, 
was asked at different times during installation.  
Maybe it was intentional confusion,m this way we would  give away our encryption pw by typing the same thing. 
 Encryption pw is important, it needs to be difficult,
 and easy to memorize for us,  and creating 2 such pw's would be enormous time of energy and time, 
and also, maybe there is a risk if they are similar.  One is encryption pw, what is the other.  //

   6. And that computer's hash code failed, not initially, but later (how strange).
 and no updates were possible.  So something was wrong from the begiinning, and then computer failed eventually. // 

  7. Windows asking too much during installation, asking email, second email, name, phone, etc forcing us to connect to internet,..  
all extreme attacks and disrespects for all humanity. Does similar things happen in new linux insallations as well. 
 I mean, forcing us o connect internet etc. It would be a great method to steal encryption and user pw. //

   8. Do we know there is no backdoors to encryption? Any difference between encrypting home directoy or not?  //   

9. Let's say I installed linux once, created partitions etc..and later, for some reason, or no reason, 
 decided to erase all, and install everthing again. Will old partitions create problems later?  
They are supposed to be erased.  //

  10. Data is encrypted, we login, they are decrypted so we can use it. 
 Does this cycle of en-de/crypting make the computer age faster, because it could mean rewriting on hard disk ?   
Also it would be great if I could separate contents of this message with blank lines without using scripts. 

 unrelated: 

 11. Ok new computers don't have removable battery, which is very bad.  Because they want electronics to be always on, for obvious purposes. BUT, WHY remove CD/DVD reader/writer from all computers. PLUS, there is no alternative method to do it either.   Everything blootoothed with convenience of instant always connection to FB, YT, L-I, all our digital IDs, like emails,.. pushed down our throats, and linux community is silent about it. who is running this world.  Can't we protest all those, or are we part of it all.  Ok, this is too long, so I don't expect a ful answer at once. a collection of partial answers can be very useful and appreciated in advance. For example you can pick an item and only respond to it. And I want to be able to install linux on any computer (and maybe on smartphones in the future), so not asking what to do on a specific brand of laptop at the moment.

---

### Post by aljames2 on 2023-07-02
Hi bjngchn

A lot here.  Here are some Ubuntu tutorials to help you create your install media and verify your download from within Windows.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

Before getting too far into the weeds, you should let readers know if you plan a dual boot system, and perhaps a little bit of info on the hardware you are installing on to.

As for this..
> **bjngchn said:**
> 11. Ok new computers don't have removable battery, which is very bad.  Because they want electronics to be always on, for obvious purposes. BUT, WHY remove CD/DVD reader/writer from all computers. PLUS, there is no alternative method to do it either.

I got rid of my CD/DVD r/w years ago.  Some still find a use for them to use older media still stored on them, or to write playable media to DVDs such as family videos, etc. but with the low cost of USB storage & speed copared to the plastic, I think they have just fallen a bit out of the mainstream.

> **bjngchn said:**
> ...Everything blootoothed with convenience of instant always connection to  FB, YT, L-I, all our digital IDs, like emails,.. pushed down our  throats, and linux community is silent about it. who is running this  world.  Can't we protest all those, or are we part of it all.

As for producers and consumers. Companies create products and consumers decide what they want to use.  Many people know very well all the data they are voluntarily handing over to Zuck and the rest, but feel it's worth it for the experience they enjoy.  I do not participate in the consumption of social media, I do not want to give them photos of when I was a child & all the other goings on in my life.  However, many people are soaked up in it.  I do not however, think it is a problem the Linux community needs to fix (which it can't), or protest, other than individuals protesting by their choice of consumption. I think it's just another product people choose to use. My two cents.  Now AI, that is another whole can of worms, for another thread someday :)

---

### Post by yancek on 2023-07-03
There are a number of software programs to write a downloaded Linux iso file to a usb stick using windows.  Unetbootin, Rufus, Ventoy, Universal USB installer to mention a few.  Google will give you a number of option.  The iso should be downloaded to the windows user downloads directory.

How to check the hash will be on the Ubuntu download page and will show once you select download as seen on the link below.

  [https://ubuntu.com/download/desktop/thank-you?version=22.04.2&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=22.04.2&architecture=amd64)

You will need to access the BIOS before booting the Ubuntu install flash drive to set it to first boot priority, probably the UEFI setting if a newer computer.  There may be other settings that need to be changed but that varies with the manufacturer.

Can't say anything about the encryption passwords as I don't use it.

No personal information will be requested such as email, tel. number, etc. 

Installing over a current OS can be done with the Erase disk and install Ubuntu option which removes everything including the partition table and partitions.  If you are installing to the same drive as windows, there should be an option to Install Alongside if the windows install is detected.  If windows is hibernated (which is the default) it will not be detected by the Ubuntu installer.

---

### Post by bjngchn on 2023-07-04
Ok now limiting my questions to creating USB stick, verifying it, and using it. 


12. Do I need Rufus to burn ISO file into flash disk? 
 Why is this needed, it must be part of the file. 
 In the past I would just click on it, and write onto flash or CD or DVD. 
Why use or trust an external service. ///////////////// 

13 .Also verifying my download looks too complicated.  I don't understand any part of it. /// 

14. I don't even see a terminal window on this linux computer. 
There is no search function to locate or browse anything. /// 

15. How likely is it the case that hash code doesn't match after downloading ubuntu file into windows computer, or any other computer. 

16. Can I check this after burning, and installing (on new ubuntu laptop). 

17. Can I use the same flash disk on multiple computer? 


18. Do downloads vary from one download to another. 
I mean, are they exactly same, or supposed to be exactly same, or can they be different, or should they be different. 
If they can be different, can they be essential things, or can they be "inessential things" used to identify those files, 
or their burnt versions, or ubuntu installations. 
For example if I use the same flash disk to install ubuntu on multiple compuers,
can this be detected on network or using another method?  Can it contain info about my IP, location,.. etc?  
Maybe ubuntu part is safe but  Rufus is adding such stuff when burning.

---

### Post by bjngchn on 2023-07-04
Ok, I found 14: terminal. It is called powershell. Also found search function, it is the  blue window image on the panel.

---

### Post by bjngchn on 2023-07-04
Ok downloaded iso file, hash done. now need to burn. As asked above, why need Rufus, or another program.  Can we use a flash disk which is not empty, to burn the file?  How does the computer know/decide there is a bootable disk, and which file to use on that flash disk.

---

### Post by ActionParsnip on 2023-07-04
> **bjngchn said:**
> Ok downloaded iso file, hash done. now need to burn. As asked above, why need Rufus, or another program.  Can we use a flash disk which is not empty, to burn the file?  How does the computer know/decide there is a bootable disk, and which file to use on that flash disk.

Because the file is data. You need to configure the storage with the data as well as setup a bootloader. You will need a flash disk to put the data onto.
The BIOS will be told to boot the USB by yourself and the boot information (created by Rufus) will be read.

---

### Post by bjngchn on 2023-07-04
RUFUS has a strange  error which is not covered in the guide.
 It almost forces me to connect internet for a better grub.
 I'm not allowed to copy paste the text WHY?: 


ANYWAY here is what it says:
.........................................
   This image uses
 Grub x.y-ubuntu-z
 but
the application only includes installation files for 
Grub x.y

(here x, y, z are numbers or strings of numbers)  

As different versions of Grub may not be compatible with one another , and it is not possible to include them all, Rufus will attempt to locate a version of Grub installation file (core.img)
that matches one from your 
image.
1. select YES, to connect to the  internet  and attempt to download it.
2. select NO, to use default version from Rufus
3. CANCEL to abort

note:if no match found, default one will be used.
......................................
So questions: 
-Can this be a trick to do something bad.
Can it be used to do something bad.  For example, can hash be changed with this?

-Why does Rufus mess with this, this is none of their business, their job is to burn, not play with someone else's file.
Ubuntu file should be complete by itself, why add something more via Rufus. This is total nonsense.

-What if I say NO, will anything go bad now or in the future? What can happen. 
I mean isn't Ubuntu download complete and only with external file it can become complete.
How reasonable is this at all.

Something fishy going on.

---

### Post by Impavidus on 2023-07-04
12: The .iso file contains an entire filesystem. This filesystem has to be put on the live disk directly, not inside the filesystem that's already on the usb drive. Tools to do so are built-in on Linux, but maybe not on Windows. I don't know Windows very well. There are in some cases some workarounds. If the computer already runs Ubuntu, you can use Ubuntu's bootloader to boot the .iso directly.

15: If downloaded on a weak wifi connection, errors are common. On a good wired connection, errors are uncommon. If you downloaded using torrent, no errors should be present, as each chunck is checked automatically and redownloaded if any errors are found.

16: You could check the usb drive later but if any errors are present it's likely the installation will fail, so better to know before attempting installation.

17: The same live disk can be used on as many computers as you like. The hardware has to be compatible, that's all.

18: Canonical promises us that a released live disk image won't change, except when the version number is changed.

---

### Post by Impavidus on 2023-07-04
> **bjngchn said:**
> RUFUS has a strange  error which is not covered in the guide.
 It almost forces me to connect internet for a better grub.

If rufus doesn't work properly, try a different tool. There are several. The only thing the tool has to do is to clone the .iso to the usb drive, but most tools like to offer additional services, which sometimes fails.

I've no personal experience with this, as I've never created a live usb on a Windows computer.

---

### Post by Rubi1200 on 2023-07-04
> **bjngchn said:**
> RUFUS has a strange  error which is not covered in the guide.
 It almost forces me to connect internet for a better grub.
 I'm not allowed to copy paste the text WHY?: 


ANYWAY here is what it says:
.........................................
   This image uses
 Grub x.y-ubuntu-z
 but
the application only includes installation files for 
Grub x.y

(here x, y, z are numbers or strings of numbers)  

As different versions of Grub may not be compatible with one another , and it is not possible to include them all, Rufus will attempt to locate a version of Grub installation file (core.img)
that matches one from your 
image.
1. select YES, to connect to the  internet  and attempt to download it.
2. select NO, to use default version from Rufus
3. CANCEL to abort

note:if no match found, default one will be used.
......................................
So questions: 
-Can this be a trick to do something bad.
Can it be used to do something bad.  For example, can hash be changed with this?

-Why does Rufus mess with this, this is none of their business, their job is to burn, not play with someone else's file.
Ubuntu file should be complete by itself, why add something more via Rufus. This is total nonsense.

-What if I say NO, will anything go bad now or in the future? What can happen. 
I mean isn't Ubuntu download complete and only with external file it can become complete.
How reasonable is this at all.

Something fishy going on.
This is normal behavior from Rufus. There is nothing nefarious about it that I am aware of.
However, if you do not trust it then use another tool to burn the ISO images.
I've not used this tool but it is portable, meaning nothing is installed on the computer, and I have seen others recommend it:
[https://portableapps.com/apps/utilities/balenaetcher-portable](https://portableapps.com/apps/utilities/balenaetcher-portable)

---

### Post by oldfred on 2023-07-04
New computers are UEFI, even though many vendors may still call it BIOS. Many now are UEFI only.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.

UEFI boots using an ESP - efi system partition. It looks for bootable files in the ESP.
Old BIOS just knew to jump to MBR or first sector of a drive for more boot code.

Often various setting in UEFI are required. I have posted them many times. But i got a  newer Dell with 11th gen Intel and forgot to make the changes and it just worked. You may or may not now need UEFI settings changed.
I did have to turn bitlocker and fast start up off in Windows.
Some good detail on UEFI & Windows settings needed - by tea for one
[https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324](https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If terms not familiar, I have a list of Acronyms with short explanation & link to more detail at bottom of link in my signature.

---

### Post by bjngchn on 2023-07-04
Used RUFUS with NO option. it worked, not sure if it would create problems.
Can I encounter problems related to that error:
Grub version mismatch?
And if so, isn't this Ubuntu's fault?
or is it just not so?
And can sudo update fix this?
Does it require fix?
/////

  Now there is a new problem, I decided to erase the entire disc and use it for ubuntu. 
 (I would prefer kubuntu, is there a way to install kubuntu instead?)  ///// 

I chose encrypted installation. I chose a security key (encryption key, but they don't call it encryption key).
  I start the computer, type  the long encryption pw; and then type user pw. 
Then I see only 2,1 GB is encrypted. 500GB remains unencrypted. 
What a nonsense. What am I encrypting here. Only 2 GB? ///////////////

 I hate lots of things: lots of junk is put on my face, while most basic things, like shut down, logout, manage users, ... are all hidden or very difficult to find.
 I search for users, the compouter tell me stories instead of showing me user link. /////////////// 

Another thing I hate, there is no way to view ROOT directory using file manager.  /////

 Also it is not clear how i can disable lots of junk like chat.
 Instead of "disable chat whatsoever", I am shown things like "make sound when i'm away".
 I don't want this computer to access any location on internet  without my decision or consent or knowledge.
 But by default such things may  happen and I will never know it.

---

### Post by ActionParsnip on 2023-07-04
> **bjngchn said:**
> Used RUFUS with NO option. it worked, not sure if it would create problems.
Can I encounter problems related to that error:
Grub version mismatch?
And if so, isn't this Ubuntu's fault?
or is it just not so?
And can sudo update fix this?
Does it require fix?
/////

  Now there is a new problem, I decided to erase the entire disc and use it for ubuntu. 
 (I would prefer kubuntu, is there a way to install kubuntu instead?)  ///// 

I chose encrypted installation. I chose a security key (encryption key, but they don't call it encryption key).
  I start the computer, type  the long encryption pw; and then type user pw. 
Then I see only 2,1 GB is encrypted. 500GB remains unencrypted. 
What a nonsense. What am I encrypting here. Only 2 GB? ///////////////

 I hate lots of things: lots of junk is put on my face, while most basic things, like shut down, logout, manage users, ... are all hidden or very difficult to find.
 I search for users, the compouter tell me stories instead of showing me user link. /////////////// 

Another thing I hate, there is no way to view ROOT directory using file manager.  /////

 Also it is not clear how i can disable lots of junk like chat.
 Instead of "disable chat whatsoever", I am shown things like "make sound when i'm away".
 I don't want this computer to access any location on internet  without my decision or consent or knowledge.
 But by default such things may  happen and I will never know it.

You can view the root of the file system but you really won't need to. As a user you will need your data in your home folder.
The system will periodically check the Web for updates to keep you aware of updates. You can disable this easily. Otherwise all the things you have said are default.
As you logout the display manager stops so you see some text. This isn't a bad thing. Just let the system do it's thing.

---

### Post by bjngchn on 2023-07-04
Ok, why was only 2.1 GB encrytped. Who would bother encrypting a fraction of the disk. I'm shown shortcuts to SSD1, SSD2, etc. This doesn't make any sense either , at least in daily use. I need shortcuts to things like, firefox, terminal, dolphin, kaffeine,  etc. Games and softwares are shown to me one by one as if I would ever use them.  This is like in a home there is no water or electricity or bathroom, but there are fancy posters everywhere on walls.

---

### Post by ActionParsnip on 2023-07-04
> **bjngchn said:**
> Ok, why was only 2.1 GB encrytped. Who would bother encrypting a fraction of the disk. I'm shown shortcuts to SSD1, SSD2, etc. This doesn't make any sense either , at least in daily use. I need shortcuts to things like, firefox, terminal, dolphin, kaffeine,  etc. Games and softwares are shown to me one by one as if I would ever use them.  This is like in a home there is no water or electricity or bathroom, but there are fancy posters everywhere on walls.

You can encrypt as little or as much as you like. You don't have to encrypt the full disk. You can even make a separate filesystem for /var and ONLY encrypt that if the fancy takes you.
Have you noticed how you make all these ridiculous statements like "it's impossible to see the root file system" when it is possible, and "it makes no sense" when it more than likely does.
Try leaving your opinions and other nonsense out and just state the situation. We can help better and it saves us having to wade through what you think is or isn't a good or bad thing.
Can you do that?

---

### Post by bjngchn on 2023-07-04
Ok, I chose "erase the disc" and "encrypt" option, then the whole disk must have been encrypted. I was not asked whether you want to encrypt this part only etc. .. I want to see Root folder, to be able to view list of users, and check which ones can be accessed directly, without using command line.... In the past I would use alternative downloads, which contained encryption option, but new versions all seem to have  that option, but there is a problem, it doesn't work.

---

### Post by ActionParsnip on 2023-07-04
> **bjngchn said:**
> Ok, I chose "erase the disc" and "encrypt" option, then the whole disk must have been encrypted. I was not asked whether you want to encrypt this part only etc. .. I want to see Root folder, to be able to view list of users, and check which ones can be accessed directly, without using command line.

I'm guessing you are using Nautilus which I've not used in absolutely ages (I'm a terminal guy) but a quick Google shows that maybe CTRL + L will show the raw file system location in the top of the file manager (you may also need to install gnome-tweak to enable it.... Again, not sure).
Users can be viewed in settings as far as I know but, again, I use terminal for this. Others may be able to advise better.
Side note though, even if you can view the root file system, you won't be able to change anything as your user due to access. You will need to launch the file manager using sudo so it runs as root. Be very very careful. You sound new to Linux so I don't suggest you go exploring too far until you are familiar with the operating system (I could be wrong but it's how you come across (no offence meant))

---

### Post by oldfred on 2023-07-04
While you can install a different desktop, it often then is more confusing.
If you really want Kubuntu better to just install it from scratch, I prefer Kubuntu, but every user has different opinions on best desktop. And many customize them anyhow so not really default.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

To see users:
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ id [/COLOR]
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),132(lxd),133(sam
bashare)[/FONT]
```

to see regular partitions:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,parttype

If encypted, you have to use LVM - logical volume management. That needs a few commands in terminal to see details.
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)

---

### Post by bjngchn on 2023-07-04
(thanks to everyone for responses) Ok  then, looks like 
 I will download KUBUNTU  using the laptop with fresh Ubuntu on it,
  and then erase that Ubuntu and try to replace it with new encrypted Kubuntu. /// 

 QUESTION1: Can I burn new kubuntu into the same  FLASH disk (USB)  (which has burnt Ubuntu in it) ? 
 If so, do I need to erase Ubuntu, or format the Flash disk (don't know how to format)?, or maybe this will happen automatically when burning (hopefully)

This time I will be using firefox on Ubuntu (not Windows) , to download Kubuntu ISO file. 

QUESTION2: So maybe burning can be done directly ?
 I don't want to use Rufus. Everyone say there are alternatives.
 But alternatives may their own/similar problems.
 I prefer a direct method (to burn), and it should be possible as it was in the past, why not.

QUESTION 3:  Let's say I have  a flash disk with such burnt k/ubuntu,
can I use it to open a problematic computer (with encrypted kubuntu) and view/copy files ?
By problematic I mean, computer is supposed to boot as usual, but there is a grub error (as mentioned in my previous threads),
which can be fixed by boot-repair (everyone says so, but I don't want to use it).

---

### Post by Holger_Gehrke on 2023-07-04
[LIST=1]
[*]It's a low level, block by block write. It will overwrite whatever is on the flash disk.
[*]Any program that can write to a raw device can be used. 'cp' and 'dd' on the command line can be used. There are tools like 'Balena Etcher' or 'unetbootin' which give you a GUI for this and try to minimize the risk involved like picking the wrong device file ... 
You can only write to devices that don't have a file system on them that is currently mounted. So first you have to unmount the file system if it has been mounted - which will happen automatically when plugging the flash disk in - by either selecting 'unmount' from the context menu in the file manager or by using 'sudo umount /dev/sdxn' or 'udisksctl unmount -b /dev/sdxn' then you can do 'sudo cp image-file.iso /dev/sdx' or 'sudo dd status=progress if=image-file.iso of=/dev/sdx'.
[*]Yes. And you'd actually need to use a flash disk to use boot repair.
[/LIST]

Holger

---

### Post by oldfred on 2023-07-05
If you want UEFI boot (and not old BIOS boot), you can create a FAT32 partition can extract ISO with p7zip or similar tool into FAT32 partition. It will then have a folder with /EFI/Boot/bootx64.efi which is the file all UEFI systems look for to boot external devices (and as a fallback boot entry for internal devices). 
It worked for me for several years, then stopped working as some file would not write. Now it works again, so it may depend on which version of Ubuntu/Kubuntu you are using.

I prefer the extraction especially if using a large drive. Use of dd erases partition table and makes it difficult to re-partition as data is written into partition table area that then partition tools cannot correctly use.
You typically have to use dd to zero out partition table area, to allow reuse. And if it was a large drive thinking data on rest of drive would be ok, it is not as partitions are gone.
Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) & 
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)

If not wanting to use Boot-Repair, you can chroot (CHange Root) to boot live installer and then use that to repair installed system.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

---

