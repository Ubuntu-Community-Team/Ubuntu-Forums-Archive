---
title: "[OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic !"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2011-05-28
[OS-UNINSTALLER]("https://help.ubuntu.com/community/OS-Uninstaller") is a small graphical tool to uninstall any OS (Windows, MacOS, Ubuntu, other GNU/Linux ..) in 1 click !

Enjoy ! :D

[IMG]http://doc.ubuntu-fr.org/lib/exe/fetch.php?hash=8f28e8&w=100&media=http%3A%2F%2Fpix.toile-libre.org%2Fupload%2Fthumb%2F1312539072.png[/IMG]

Screenshot :
[[img]http://pix.toile-libre.org/upload/img/1313035409.png[/img]](http://pix.toile-libre.org/?img=1313035409.png)


**Download/Install OS-Uninstaller in Ubuntu :**
either add &#8216;ppa:yannubuntu/boot-repair&#8217; to your Software Sources via the Software Centre or, for speeds-sake, add it using a new Terminal session:

* sudo add-apt-repository ppa:yannubuntu/boot-repair
* sudo apt-get update && sudo apt-get install -y os-uninstaller


OS-Uninstaller can be installed & used from any Ubuntu session (normal session, or live-CD, or live-USB).

PPA packages are available for current versions of Ubuntu.

**Use OS-Uninstaller:**
Launch it from System->Administration->OS-Uninstaller menu if you use Gnome, or search "os" in the dash if you use Unity. Then follow the menus...


**You can contribute by** :
- voting on Launchpad for these bugs: [1st]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/806291"), [2nd]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/747279"), [3rd]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/653474"), [4th]("https://bugs.launchpad.net/os-uninstaller/+bug/823152")
- [translating]("https://translations.launchpad.net/boot-repair/trunk") (now ~60 languages)
- suggesting improvements

---

### Post by sikander3786 on 2011-05-28
Wow, that sounds good. Thanks :)

I would want to try it but I don't have anything to un-install right now.

I would add my testimonial if I get a chance and if anybody else gets it, please add.

Just to make sure, it doesn't mess up the bootloader, right?

**Added:** Ok, for my queries, I'd follow this thread so you don't have to answer it all over again. Also, you could add a link to that one in the above post?

[http://ubuntuforums.org/showthread.php?t=1615667](http://ubuntuforums.org/showthread.php?t=1615667)

---

### Post by YannBuntu on 2011-05-28
> **sikander3786 said:**
> it doesn't mess up the bootloader, right?

Of course not, you can check the "Advanced options". On the contrary, I would say I developped this app because some people thought they could uninstall any OS by simply deleting its partition, which of course caused problems with their boot ;)

> **sikander3786 said:**
> [http://ubuntuforums.org/showthread.php?t=1615667](http://ubuntuforums.org/showthread.php?t=1615667)

This Remix includes OS-Uninstaller (and Boot-repair) by default, but its main goal is to include Clean-Ubiquity.
OS-Uninstaller can be installed in any Ubuntu version or derivative, so I prefer to keep this thread focused on OS-Uninstaller only. :)

---

### Post by YannBuntu on 2011-08-09
Hello, a new version is now ready.
**I need everyone's help to translate this tool in your language !**

---> [https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

Thanks in advance :)

---

### Post by hakermania on 2011-08-09
> **YannBuntu said:**
> Hello, a new version is now ready.
**I need everyone's help to translate this tool in your language !**

---> [https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

Thanks in advance :)
already translated in greek. Have you thought to package it and send it for review for inclusion to the repositories?

---

### Post by YannBuntu on 2011-08-09
Thanks ! Yes, I will propose this app to Debian&Ubuntu reps, but before I will wait several days for the translations to be completed :)

---

### Post by hank22077 on 2011-08-18
Actually, this is an awesome tool. I somehow screwed up my Ubuntu install with updating...?:confused: ; couldn't get my computer to boot @ all. Which woulda really 'peed' my wife off since she still uses Vista! Anyway, I used an Ubuntu CD to get things booted, get on net, find this page; downloaded and got everything fixed! Thanks for this tool.

Only one thing, I've got 10.04 LTS, I added it through PPA, but don't see it in my System-> Admin menu...any idea why?

---

### Post by YannBuntu on 2011-08-18
@hank22077:  thanks for your feedback, and happy it helped. Concerning the icon : what language do you use in your Ubuntu ? can you type the following command:
```
ls /usr/share/applications | grep "ler"
```
and tell me the result ?

---

### Post by hank22077 on 2011-08-18
:lolflag:
It's English. But...Actually, I went to **System > Administration > Software Sources > Other Software** to add &#8216;ppa:yannubuntu/os-uninstaller&#8217;. I guess that's why it didnt show.
I got smart n thought "make it simple, stupid", and realized : Applications -> Ubuntu Software Center, found it and installed it. So now it shows in my menu.

Thanks, again

**BTW**
Result: 
ls /usr/share/applications | grep "ler"
file-roller.desktop
gnome-theme-installer.desktop
nautilus-folder-handler.desktop
os-uninstaller.desktop

I'm new to Ubuntu, and a 'low-level' web designer, so I assume that was a call to show results for things ending in "ler"...? Checking if uninstaller would come back...?

---

### Post by YannBuntu on 2011-08-18
glad to see you found a way to get the icon. :KS
And nice to see you are curious about commands, that's how I learned too ;)  the command lists all files containing "ler" in the folder /usr/share/applications . So you can see you have a "os-uninstaller.desktop" file, which is an entry for "OS-Uninstaller" in your menu.

---

### Post by jimmygotlucky88 on 2011-10-12
Will this uninstall Windows 7 from a dual boot Wubi installation? It gives me the option to delete Windows 7(sda1), but.... will it also delete my ubuntu since it is actually inside of the partition? Please help.

---

### Post by YannBuntu on 2011-10-12
Hello Jimmy,
Yes, removing Windows will also remove your Ubuntu installed via Wubi.
(This information will be displayed in the confirmation window that will appear after you choose the OS to uninstall.)

---

### Post by Elfy on 2011-10-12
> **jimmygotlucky88 said:**
> Will this uninstall Windows 7 from a dual boot Wubi installation? It gives me the option to delete Windows 7(sda1), but.... will it also delete my ubuntu since it is actually inside of the partition? Please help.

You need to install ubuntu properly rather than as wubi to do that, though there is the possibility of moving it to a new partition. 

You'd be better starting a thread for that.

---

### Post by YannBuntu on 2012-05-04
For information, if you were blocked with OS-Unninstaller on 12.04 after choosing the OS to remove, the solution is simply to update OS-Uninstaller.

---

### Post by YannBuntu on 2012-05-09
Added warnings concerning formating:

[[img]http://pix.toile-libre.org/upload/img/1336577243.png[/img]](http://pix.toile-libre.org/?img=1336577243.png)

[[img]http://pix.toile-libre.org/upload/img/1336577469.png[/img]](http://pix.toile-libre.org/?img=1336577469.png)

---

### Post by nll on 2012-07-03
In the four+ years I've been using Ubuntu, only once I had problems with Grub. I was annoyed by it at first, but then I found Boot Repair and fixed the problem without a sweat. Now I need to uninstall Ubuntu from an old computer, and I'm sure OS-Uninstaller will be very handy.

Thank you very much for those great tools, YannBuntu! They should not only be in the repositories, but also be default in the Ubuntu ISO and be further integrated in Ubiquity.

---

### Post by YannBuntu on 2012-07-04
Glad it helps :)
if you want, you can mark yourself as "affected" by this bug: [Boot-Repair pre-installed in ISOs]("https://bugs.launchpad.net/boot-repair/+bug/806291")

---

### Post by nll on 2012-07-04
I've already done it! :p

Isn't there a similar bug requesting OS-Uninstaller to be pre-installed on ISOs?

---

### Post by YannBuntu on 2012-07-04
yes: [https://bugs.launchpad.net/os-uninstaller/+bug/823152](https://bugs.launchpad.net/os-uninstaller/+bug/823152)

---

### Post by YannBuntu on 2012-09-17
**@all:**
I need your help to continue improving OS-Uninstaller (and Boot-Repair):
[http://ubuntuforums.org/showpost.php?p=12239465&postcount=538](http://ubuntuforums.org/showpost.php?p=12239465&postcount=538)

Thanks in advance ! :)

---

### Post by btheboat on 2012-10-22
Hi there,

In attempting to uninstall my windows partition i received the message that I would have to update my bootloader.
Is this because my Ubuntu is installed on windows via wubi (sda3)?  Windows is on sda2.

Im hesitant to do anything until I know for sure what I will lose.

Cheers.

---

### Post by YannBuntu on 2012-10-22
Hello
Wubi installs Ubuntu INSIDE Windows (even if you told it to use a different partition, it uses the Windows bootloader).
So if you installed Ubuntu via Wubi, removing Windows will break access to your Wubi/Ubuntu. OS-Uninstaller will warn you if you try to remove Windows. 
Example:
[IMG]http://pix.toile-libre.org/upload/original/1350929205.png[/IMG]

If you installed Ubuntu via Wubi, and you want to get rid of Windows, you have to:
1) backup your documents on an external disk or DVDs
2) format your disk (eg via Gparted)
3) Install Ubuntu the standard way (without Wubi): [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by btheboat on 2012-10-23
Hi,

Brilliant, thanks very much.  That worked perfectly and I now I have a windows free computer.
Thanks for the help.

---

### Post by CableguyJ on 2013-01-04
Thank You very much YannBuntu, worked like a champ. Followed instructions on Community Ubuntu removed Lucid Lynx, and Windows works fine. Now I can try Precise Pangolin. :D

---

### Post by twistle on 2013-01-30
If I'm uninstalling Ubuntu from a Ubuntu/W7 dualboot, does OS-Uninstaller really restore the windows bootloader or would have to manually restore it with a Windows installation CD (which I do not have)? The OS-installer dialog says "Then you will need to update your bootloader", which somehow leads me to belive it's the latter :/

---

### Post by Mark Phelps on 2013-01-31
You CAN create your own disk by using the Backup feature in Win7 to create and burn a Win7 Repair CD.

If you can't boot into Win7 after removing Ubuntu, insert this repair CD, boot from it and run Startup Repair three times -- that's right, three times.  It takes several passes to make all the repairs needed.

---

### Post by YannBuntu on 2013-01-31
hi
> **twistle said:**
> The OS-installer dialog says "Then you will need to update your bootloader"

That means that os-prober detected several Windows instances, probably loader and recovery.

Please follow Mark's advice.

---

### Post by twistle on 2013-02-01
Okay, thanks for your answers.
I also don't have CD-drive, so this wouldn't have worked for me, which is a pity! I ended up using EasyBCD instead, which was more than one click, but worked all the same :D

---

### Post by YannBuntu on 2013-02-01
good job. For information, Boot-Repair-Disk and Ubuntu-Secure-Remix  (which both contain OS-Uninstaller) can also be put on a live-USB.

---

### Post by MintTea on 2013-05-19
[SIZE=3][FONT=courier new]Yann,
Thanks: it helped a lot (and was easy to use). [/FONT][/SIZE]

---

### Post by cthornett on 2013-08-06
Just wanted to post to say thanks for this. For a Linux noob like me it made uninstalling really easy. Thanks!

---

### Post by dougal2 on 2013-08-22
Hello Folks. I am about to attempt to uninstall Ubuntu. I have a dual boot windows 7/Ubuntu I believe?? When I boot up it gives me the options of which OS I want to choose. Also I don't see Ubuntu anywhere in my programs under programs and features. However I just looked in my bootable drive where I installed Ubuntu and there is a file titled Wubi.exe. Hopefully someone can tell me if I do have Ubuntu within windows or I did install it as a dual boot? Thx Dougal

---

### Post by oldfred on 2013-08-22
Wubi is the file within the Windows NTFS partition. You should be able to just uninstall from Windows like any other program. You may need to edit BCD to remove boot entry, but that is all Windows and Boot-Repair or uninstaller does not do that.

More info:
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by dougal2 on 2013-08-22
Thanks oldfred. I will look into Wubi more before I uninstall

---

### Post by pablo.fiumara on 2013-10-29
Thanks for this tool!

I had this doubt: 

> What would happen after I uninstall **all** the OS using OS-Uninstaller? For more information about OS-Uninstaller, you can visit [the wiki]("https://help.ubuntu.com/community/OS-Uninstaller") and [Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1769489&p=10871988#post10871988")
  Will I be able to **boot** from USB or CD so that I can make a fresh install of an OS? I wish to do it before doing a fresh install of an OS. 



And this is the answer I received: 

> All OS Uninstaller does is nuke disk partitions that it detects. It  doesn't stop you booting to media like USB or CD... Assuming you don't  nuke the USB partition.



[http://askubuntu.com/questions/367888/what-would-happen-after-i-uninstall-all-my-os-using-os-uninstaller-will-i-be-ab](http://askubuntu.com/questions/367888/what-would-happen-after-i-uninstall-all-my-os-using-os-uninstaller-will-i-be-ab)

Actually, I was told by the creator of this tool that if one wants to uninstall all the OS, one can just choose "Erase disk and install Ubuntu" from the LiveDVD. [https://help.ubuntu.com/community/GraphicalInstall#Installation_type](https://help.ubuntu.com/community/GraphicalInstall#Installation_type)

---

### Post by pablo.fiumara on 2013-10-29
I uninstalled Windows 7 using this tool. I had two options: Windows 7 and Windows 7 recovery enviroment (or something like this). The tool succeeded in uninstalling Windows 7 when I removed first the enviroment and then the OS. 

I hope someone finds this useful.

---

### Post by NM5TF on 2013-12-20
thanx Yannbuntu for another GREAT tool....just what I was looking for !!!

used it twice this morning to remove Win XP from Wife's laptop after
installing Ubuntu 12.04.3...and on my Desktop to remove Mint 14 after 
installing Mint 16....

couldn't be easier to use & it's failsafe !!!

Tommy

---

### Post by MercuriusAurelio on 2014-02-23
I've looked all over the net for a solution to this, but I can't figure out how you make a live USB with OS uninstaller, and I get the message "please use this software in a live session". can anyone point me in the right direction?

---

### Post by oldfred on 2014-02-23
Any Linux liveCD/DVD/Flash will work.

You can download a live version.
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
Link in above to the secure remix
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

Ubuntu 

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by MercuriusAurelio on 2014-02-24
So I have to make a bootstick with linux remix just to be able to use OS uninstaller?

---

### Post by oldfred on 2014-02-24
It is just an app running on Linux, not a full bootable system.

This now may not be current, but will still work.
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Full Boot-Repair also included os uninstaller.
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by andrew.t.sullivan on 2014-03-07
Yannbuntu

This looks like a very useful tool, thanks.

I have W8.1, openSuse 13.1 and Ubuntu 13.10 on my laptop.  I rarely use the first two OS and every time I update openSuse it messes up the boot process so that I can't boot into Ubuntu...

I propose to try OS-uninstaller to get rid of openSuse - do you forsee any problems?  Do I have to run boot-repair afterwards?  If it matters I have Secure Boot enabled on the laptop.

Thanks in advance.

Andrew

---

### Post by andrew.t.sullivan on 2014-03-12
Anybody????

---

### Post by oldfred on 2014-03-13
I have not seen Yann around lately. 

Have not seen may use Os_uninstaller so do not know details. It was more to install new grub or Windows into MBR somewhat like Boot-Repair. Not sure if it does any of the UEFI updates, but since some details are not obvious to a program, it may just be best to manually update. It also does not delete or reorganize partitions which you may want to do.

But have seen many use Boot-Repair with UEFI whether secure boot is on or not. But it is running chroots and grub installs. It does not delete partitions. Even grub does not modify UEFI boot order and it seems that Windows does modify UEFI boot order as it keeps becoming first on updates.

With UEFI every system has boot loaders in efi partition. Usually you have to manually delete folder with system you want to delete, and manually update UEFI NVRAM as it auto updates from efi folders. You also have to set default boot order in UEFI.

       Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated


 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by andrew.t.sullivan on 2014-03-13
Thank you for your reply - food for thought there!

Andrew

---

