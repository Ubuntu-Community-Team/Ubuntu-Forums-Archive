---
title: "How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by mgmiller on 2014-06-11
I spent a few days figuring all this out from many sources and thought I would give it back to the Ubuntu community.  YMMV as they say, so good luck with my 18 or so easy steps.....

My goal was to install Ubuntu 14.04 by itself on a RAID 1 array of2 HDD's using the motherboards built in RAID controller.  (Fake RAID,software RAID)
Hardware:  MSI Z87-G41 PC Mate mobo with intel Z87 chipset.  Inteli5-4670k LGA1150, 2-WD Black WD5003AZEX S3 500G HDD's, 8GB crucialRAM.

First Part is motherboard configuration:
Configure the Intel RAID as RAID1 with 2 HD's, by doing the following (if you have a different mobo, the exact steps will be a little different, but the concepts are the same.  &#8220;Where's the damn anti matter inducer?"  "This? No...this!&#8221; "That or nothing.":
First, set up your BIOS by booting and hitting the Delete Keyuntil the bios is visible.  In integrated peripherals, select thehard drive controller and set it to RAID.  Use esc key and saveconfiguration and exit.  Next, reboot and keep holding the Ctrl keyand repeatedly hitting the I (letter i) key until the intel RAIDconfiguration screen appears.  If you're not quick enough, you mayneed to reboot a few times to get it to work, as it flashes by veryquickly.  Use the tab & up-down arrow keys to select the 2 drivesand set them to the configuration you want.  I used RAID 1.  Finally,boot back to the BIOS configuration screen again and  go to the bootsection and select the boot order with USB key as first and the RAID array, which will show as a single entry named Intel HDD as the second boot device.  Save configuration & exit.

Second Part is software RAID configuration:
Boot the Ubuntu installation live CD/USB thumb drive whileconnected to the Internet (**very important, you need toinstall packages from the repository!!!**).

[LIST=1]
[*]When the installation boots up    choose "**Try Ubuntu**"
[*]Make sure you are connected to the    internet (**again, crucial step**)
[*]Open a terminal and type the following to temporarily disable dmraid and install mdadm.
[/LIST]
```
sudo dmraid -a n
```
```
sudo apt-get install mdadm
```
 

[LIST=1]
[*]You will be prompted with POSIX    configuration, I chose No Configuration.  This is a DOS type screen that you navigate in with the tab, arrow, space bar and enter keys.
[*]Wait for it to finish and type in the terminal to automatically recognize and set up your FakeRAID:
[/LIST]
```
sudo mdadm --assemble --scan
```

There is no need to reboot at this point.


Third Part...We are now ready to start the Ubuntu installation: 

[LIST=1]
[*]Run Install Ubuntu from the    desktop icon or the top icon on the launcher.
[*]Choose to Install Ubuntu
[*]Choose to partition manually and    create: 50 MB bios boot partition with bios_grub flag (reserved bios    area) followed by a 200 MB EFI boot partition at the front of the    drive, a swap partition of appropriate size at the end of the free    space and the remaining free space as an EXT4 partition mounted as / .
[*]When choosing where to write the Boot-Loader - Choose the    volume mounted as &#8220;biosgrub&#8221;.  This is not going to work and    will cause an error in the installation, but you will fix it later.
[*]Proceed with the installation.
[*]After all this, the installer will fail to write GRUB and    give you a fatal error.  The installation can go no further.
[*] Reboot using the live installation disc/USB thumb drive,    connect to the Internet, install Boot Repair by opening a terminal    and copy/paste the following lines one at a time followed by the    enter key:
```
[COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:yannubuntu/boot-repair[/FONT][/COLOR]
```
```
[COLOR=#333333][FONT=UbuntuMono]sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list[/FONT][/COLOR]
```
```
[FONT=UbuntuMono][COLOR=#333333]sudo apt-get update[/COLOR][/FONT]
```
```
[FONT=UbuntuMono][COLOR=#333333]sudo apt-get install -y boot-repair && (boot-repair &)[/COLOR][/FONT]
```
[*] (If needed, you will find complete instructions online    here.... [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ;).
[*]Launch Boot Repair (it may launch itself at the end of the    last command above) and it will guide you on fixing the boot loader    and rewriting GRUB.  Note that this will switch you back from mdadm    to dmraid.  I had to run boot repair twice to fix everything. After    it's first attempt, it said grub was not installed and suggested I    try again.  If Boot repair has exited, rerun it by hitting the super    key (windows key...sigh)  and typing boot.  It's icon should appear.     The second attempt did it after I installed grub on all listed hard    drives when the dialog to do so appeared.  Use space bar up/down and    tab to select different bootable devices by putting an * inside the    [ ] next to the drives you want to put grub on, tab down to the ok    symbol and hit enter. The only thing I didn't put grub on was the    USB key the live session was running from.
[*]Because the initial installation failed before it could    complete, reboot with the live disc/USB thumb drive again and select    the option to &#8220;reinstall Ubuntu&#8221;.  It may seem to stall out    towards the end where it says &#8220;Restoring previously installed    packages...&#8221;.  It took my system about 15 minutes to clear this    step, but it could take longer (over an hour) depending on your    system specs and Internet connection.
[*]Finally, it completes and you have the option to reboot.     Don't forget to take out the live disc.
[*]  You should  now be booted on the RAID on your desktop.  
:guitar:

If someone wants to put in the experimentation time, you may be able to simplify the above, but I am just glad it worked after doing all that.  I am also considering just chucking the whole install and buying a hardware RAID card, which should dramatically simplify the whole mess.  ](*,)


The following is optional after you have the whole thing running.  There is a GUI of sorts available to control the RAID (and damn near everything else in your system), called webmin.  The example I give the first link to is for controlling RAID using mdadm, I don't know if it works with dmraid.  Read more about it here:  [http://michal.karzynski.pl/blog/2009/11/18/mdadm-gui-via-webmin/](http://michal.karzynski.pl/blog/2009/11/18/mdadm-gui-via-webmin/)
For total webmin info, look here:  [http://www.webmin.com/index.html](http://www.webmin.com/index.html)
[/LIST]

---

### Post by mgmiller on 2014-06-18
As I mentioned above, I did get a real Hardware RAID card.  It's an Adaptec[SIZE=2][FONT=arial] RAID 6405E 2271700-R 6Gb/s SATA/SAS 4 internal ports w/ 128MB cache memory Controller Card, _**Kit**_.  It's important to get the kit and not the bare card because there is a proprietary cable that attaches to the card to let you plug in your sata drives.              [/FONT][/SIZE][http://www.adaptec.com/en-us/products/series/6e/](http://www.adaptec.com/en-us/products/series/6e/)

Anyway, you install the card and plug in your drives and boot into the controllers BIOS with Ctrl A to let you set up your RAID configuration,  then reboot and go into the mobos' bios and select the array you just created and put it in the correct boot order.  I am using it in RAID 1 with 2 Samsung 840 EVO SSD's.

Reboot and install Ubuntu normally.  It just works. \\:D/

This card supports many Linux distros and includes drivers for them on an included CD.  If you are installing Ubuntu 14.04, no drivers are needed, it's all built into the kernel.  For 12.04, the drivers are on the CD.

---

### Post by SkOrPn on 2014-06-18
Hello mgmiller,

I am curious if your guide above would work for BIOS raid using ICH10R (x58 motherboard). It is NOT a EFI or UEFI system, its all pure old school BIOS here. The reason I ask is one of your steps (step 3) states to > 3. Choose to partition manually and create: 50 MB bios boot partition with bios_grub flag (reserved bios area) **followed by a 200 MB EFI boot partition at the front of the drive**, a swap partition of appropriate size at the end of the free space and the remaining free space as an EXT4 partition mounted as / .


Also, I want to create a separate partition for Windows during this step (at least 2/3rd's of the space), but not format it since Windows 8.1 will not use it without needing to create the partition itself. Can you please advise on the changes you would try? I am coming off of 3 days of work (16 hours yesterday alone, not very happy about that lol) trying to get Ubuntu 14.04 and Windows 8.1 installed on two Samsung 840 Pro's but none of the guides I have been reading are working correctly. I tried many of the steps above but did not do step 3 correctly I believe. What I did was let Ubuntu create the partitions itself, then I backed out of the installer and used gparted to resize and create the partitions how I need them to be. During the actual install, GRUB fails of course, then I try changing it to another location and then it works. Today is my fourth day since I started this, and its now a week since I started the research. Windows breaks Ubuntu's install, then Ubuntu breaks windows install and I am going back and fourth over and over trying to fix each others problems. I never did have luck with mdadm but was successful with dmraid, not sure why. Boot-Repair is not working for me either, it keeps spitting out an error message. One interesting thing to note, is my 14.04 is installing to the raid array by default out of the box without any terminal code, it just installs (except for the GRUB error). So, if I can't get mdadm to work during the install, maybe I can get this to work with dmraid (I already did in fact), and then possibly once it is finished and working, then simply "switch over" to mdadm? Currently the machine sits in a state with Windows booting and Ubuntu not booting, but both are installed on the same array and ubuntu is using dmraid and GRUB is yet again broken, thanks to Windows. lol

Any thoughts or tips would be appreciated. Thank you.

Here is my BootInfo [http://paste.ubuntu.com/7665391](http://paste.ubuntu.com/7665391)

---

### Post by mgmiller on 2014-06-18
I spent 10 solid hours getting to the point that's documented above.  I do not dual boot with Windows.  I am running Ubuntu alone.  If you are using a non-uefi mobo, I would skip the efi partition step.  I think you are very close.  You seem to have Windows installed and working and Ubuntu installed, so your partitioning is probably good.  Did you do steps 7 through 10 above?  Boot-repair is critical to making this work.  That is what ultimately fixes grub so you can get into Ubuntu.  dmraid is the default raid driver in 14.04, mdadm was only used as a temporary measure to get some kind of array that the Ubuntu installer would see.  After running boot-repair twice, it switches you back to dmraid. 

Even though I was ultimately successful, I did not really trust the fakeraid.  If it broke, I was concerned it would take me a horrendous amount of time to fix and since this is going to be my business file server, it has to be easy to administer.  That is why I opted to get the RAID card in my previous post.

---

### Post by SkOrPn on 2014-06-18
Yeah, I'm not trusting it either. On Windows it is a different story and I have never experienced FakeRAOD problems, but that is extreme amounts of money being poured into Intels Windows WHQL prgram, so it is extremely reliable. But with Ubuntu I have no clue the current status of the raid drivers.

Well, I just tried your steps above and had a totally different experience. After the 10th or so install of Ubuntu, out of the blue this time I did NOT get the GRUB failure message, it just completed the install using mdadm. I Also tried creating all these bios partitions but my setup did not have any such option. So I wiped the array clean, and then simply created two partitions, one ext and the other unformatted, leaving me with only two entries. I also was forced to use gparted instead of the installation routine. At your step 6 above I was just greeted with a Congratulations Ubuntu installed and is ready to restart. So, I restarted and the system hung, lol... This time I got quite angry, and instead of launching the live session I used the boot-repair disk and tried to go that route. Everything seemed to go OK until the moment it asked me to copy paste the apt-get install routine, which the code was incorrect, and I had to change it myself to the proper code, only to discover it was going to download nearly 500 mb/s of updates. So again my changes were wrong, however after the updates it asked me to install GRUB to the proper location (I selected every location haha), and it then told me it failed to install GRUB. However, upon reboot here I am in my Working Ubuntu installation on my Intel FakeRAID and everything seems to be working great. 

Now I have to figure out how to install Windows, on the second partition gparted created, and get my employers software re-setup before I have to report to work next Monday, lol. I am worried about re-installing Windows now as that is what broke it over and over the last few days. I also need to see if its possible to migrate from this deprecated dmraid to mdadm in the meantime. Anyway thanks for the reply. I'm going to play around with this fresh Ubuntu install and get some things organized and updated.

Oh, and yeah I want a raid card so bad, but I am going to opt for a [rebranded lsi 9271-4i]("http://www.ebay.com/itm/New-IBM-M5110-8-port-PCI-E3-0-6Gb-RAID-Card-00AE807-90Y4449-81Y4481-9211-8i-/301089132503?pt=US_Computer_Disk_Controllers_RAID_Cards&hash=item461a4f8fd7"). They are probably the fastest cards around and only about 1/3rd the cost, if not less. Just need to figure out how to flash proper LSI firmware onto it, lol...

---

### Post by mgmiller on 2014-06-19
You will certainly have a much easier time installing with a hardware RAID card.  That being said, I looked at your link and the card pictured looks nothing like either the lsi9271-4 which is shown here...[http://www.lsi.com/products/raid-controllers/pages/megaraid-sas-9271-4i.aspx](http://www.lsi.com/products/raid-controllers/pages/megaraid-sas-9271-4i.aspx)    or the IBM 5110, which it purports to be seen here... [http://www.redbooks.ibm.com/abstracts/tips0054.html#m5110](http://www.redbooks.ibm.com/abstracts/tips0054.html#m5110)   

The Adaptec card I am using was about $189 at Newegg and it is a genuine Adpatec product.  No need to reflash or hack around with anything and I have even spoken with Adaptec support about it before I got it, to answer a few questions and they were very knowledgeable and helpful.

I'm not sure what you're buying on e-bay, so be careful and good luck.

After installing Windows, if the grub gets broken again, try running boot repair again. 

I'm not sure why you felt you needed to change the code that boot repair suggested.  My experience with it is not extensive, so I can't comment on why it may or may not have been wrong, but you did get an odd result with your changes.

---

### Post by SkOrPn on 2014-06-19
[FONT=Arial][COLOR=#000000]Boot-Repair usually has two steps, the purge step and the install step. When I use Boot-Repair it spits out terminal code for the removal of GRUB which all works fine, but when it gets to the point of installing GRUB, it spits out incorrect code as is evidenced by the machine telling me an error code [/COLOR][/FONT]**[COLOR=#333333][FONT=Arial]"E: Unable to locate package linux" [/FONT][/COLOR]**[FONT=Arial][COLOR=#000000](something along those lines). I then go back to see what it did when it purged it and I realize it is giving me the wrong code to put into the terminal, otherwise it would have worked, lol. So, I edit it and it then works properly and GRUB is fixed. The command Boot-Repair gives me that fails is below

[/COLOR][/FONT]```
[COLOR=#333333][FONT=Arial]sudo apt-get install -y --force-yes grub-pc linux*[/FONT][/COLOR]
```

The one that works that I edited myself is

```
[COLOR=#333333][FONT=Arial]sudo apt-get install -y --force-yes grub-pc[/FONT][/COLOR]
```

This is of course only when I have Ubuntu installed, and not windows. Once I install Windows and re-launch the Live Ubuntu everything in Boot-Repair is then completely different and completely broken. And further if I use the installed version of Boot-Repair or the Disk version, each version gives out different repair code. So obviously it does not like something about my machine. Anyway, I just found a completely new dual boot guide specifically for 14.04 and Win 8.1, so I am going to give that a try today, and pray it works with FakeRAID. OH, I just noticed in the comments that I am not the only one with Boot-Repair problems, others are getting the same error message I am. Proof that it must be the combination of 14.04 and Win 8.1.

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html#comment-form](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html#comment-form)

[COLOR=#000000][FONT=Arial]I already installed Windows a dozen times over the last 5 days, and each time Boot-Repair would not fix it, after entering each code it gives me all I get in response are these error messages. Its time for another approach, not the same one that repeatedly fails. And when I gave up on Boot-Repair I tried using EasyBCD and it completely killed my windows install, lol... I'm going to stop using these easy UI fix methods and just use the terminal from here on out...[/FONT][/COLOR]

---

### Post by mgmiller on 2014-06-20
I am glad I don't dual boot.  In general, aren't you supposed to install Windows first and then do the Ubuntu install?  It sounds like you are doing the opposite.  I am also wondering how you are installing Windows 8.1 in an old, non UEFI bios.  I thought that was a requirement.

My final thoughts were have you considered running Windows in a vm within Ubuntu or Ubuntu in a vm in Windows?  Have you considered a wubi install (I know that's not ideal because you will be running Ubuntu in NTFS).

Good luck.

---

### Post by JSeymour on 2014-06-20
> **mgmiller said:**
> As I mentioned above, I did get a real Hardware RAID card.  It's an Adaptec[SIZE=2][FONT=arial] RAID 6405E 2271700-R 6Gb/s SATA/SAS 4 internal ports w/ 128MB cache memory Controller Card, _**Kit**_. [/FONT][/SIZE]
...
I am using it in RAID 1 with 2 Samsung 840 EVO SSD's.
The problem with that, and the reason **I** didn't finally give up on  software RAID and go with a RAID card, is no TRIM support.

No  TRIM support is a problem.  SSDs internally shuffle used blocks around to prolong the life of each...  "memory cell," let's call them.  Without TRIM, the SSD(s) will actually  shuffle-around data blocks that are unused, thus potentially  *decreasing* service life, rather than increasing it.  Without  TRIM, you'll also eventually begin to lose performance.

> **mgmiller said:**
> I spent 10 solid hours getting to the point that's documented above.
I spent considerably more time than that, messing with dmraid (which actually just worked, right out of the box--but it's deprecated, so...), and mdraid.  I was *trying* to get mdraid working with my FakeRAID array.  Finally gave up and went with native Linux RAID.

  > **mgmiller said:**
> I do not dual boot with Windows.  I am running Ubuntu alone.
So why not just use native Linux RAID?  Works like a champ, and supports TRIM for RAID levels 0, 1 and 5 (at least).

With RAID1 (mirrored, which is what I'm doing), you can even let /boot be in the RAID array.

I, also, am using a Z87-A mobo (Asus), btw.

Jim

---

### Post by SkOrPn on 2014-06-20
Yeah, it seems many people overlook the extreme importance of automatic TRIM functions. My Intel FakeRAID has TRIM enabled and is every bit as fast and stable as native Linux RAID. However, it is NOT anywhere near as good as a real RAID card as mgmiller has, but you can do manual TRIM functions I am sure. I know it is easily possible on Windows, so I assume it is on Ubuntu as well.

Well, I tried the mdadm install steps above just to see if it would install/migrate in a working dmraid environment and wow, I did not expect it to just work out of the box like that. It makes me suspicious and wondering if I am really in a RAID0 environment at the moment. Is there any way to test my internal transfer speeds (should be around 500 MB/s), or look at the raided set in a UI or terminal command?

---

### Post by mgmiller on 2014-06-20
There is a whole discussion about trim going on.  Apparently, with modern ssd's, trim is no longer necessary.  The newer drives incorporate "garbage collection", which can run independently of the RAID controller, that essentialy does what trim did.  The main difference, is that trim could run while the drive was busy, while garbage collection needs the drives to be "quiet" for a few minutes.  Since my server runs 24/7 and during the night hours, nothing is going on, the garbage collection can run easily at least once a day.  There has been a lot of discussion about this on line, and I have decided that with modern SSD's, specifically Samsung 840 EVO's I don't need to worry about trim.  Unlike trim, garbage collection does not need to be initiated from the OS.  It is built into the drives micro controller firmware and runs automatically.

---

### Post by JSeymour on 2014-06-23
> **mgmiller said:**
> Apparently, with modern ssd's, trim is no longer necessary.  The newer drives incorporate "garbage collection", which can run independently of the RAID controller, that essentialy does what trim did.
No, GC **does not** do what TRIM does.

In order for an SSD to do on its own what TRIM does, it would have to know about every different filesystem type, RAID implementation, (logical) volume manager design, etc. in existence, so it would know "when the OS marks this metadata unused, that means these other blocks are now unused."

That, in turn, would require that every time a new filesystem format, RAID implementation, LVM, etc. is created, or existing one in any way changed, new firmware would have to be downloaded and installed into *each and every SSD in a system*.

That would be neither practical nor safe.

People that argue the advent of (improved) GC obviated the need for TRIM understand neither SSD GC nor TRIM.

Jim

---

### Post by t873sm on 2014-08-19
I am using a Gigabyte GA-Z97N-WIFI mobo and not having any success.  (I am using GUI not server version, does that matter?)
I got all the way to the re-install and it successfully completes.  After reboot, it is working fine.  I start Gparted to set up my data partition of 4 2TB HDDs in a RAID10 configuration and get errors.  (I will try to write them down next try.)  The Raid with the OS is gone.  Now, the disks show up in BIOS as non-Raid.

System boots to the last disk that was in the array, but I am going to have to start over.

Any suggestions?

---

### Post by mgmiller on 2014-08-20
> **t873sm said:**
> I am using a Gigabyte GA-Z97N-WIFI mobo and not having any success.  (I am using GUI not server version, does that matter?)
I got all the way to the re-install and it successfully completes.  After reboot, it is working fine.  I start Gparted to set up my data partition of 4 2TB HDDs in a RAID10 configuration and get errors.  (I will try to write them down next try.)  The Raid with the OS is gone.  Now, the disks show up in BIOS as non-Raid.

System boots to the last disk that was in the array, but I am going to have to start over.

Any suggestions?

I assume you set up the RAID 10 in the bios before you did anything else ( First part motherboard configuration).  

Third Part step 3 is where you do the partitioning.  When I was experimenting, I found that using gparted did terrible things to the fake raid.  By waiting to do your partitioning until you were done, I think you may have negatively affected the RAID.  Good luck.

---

### Post by WinEunuchs2Unix on 2014-09-25
I quickly perused these two pages.  I have an i-7 3630QM IvyBridge with Intel Mobile Motherboard, fake raid with OROM plus Dell legacy BIOS support so you can use UEFI and MBR at the same time.  I haven't been able to do the <Ctrl>+l (lowercase L) thing to invoke the Intel Fake Raid BIOS/Firmware Setup that people keep talking about.

I too read how mdadm was intel recommended and that dmraid was going out the door in 2011.  But then in 2012 or 2013 dmraid gets added to the Kernel as standard fare with no need to "sudo get-apt install" it.  Out of the box I installed Ubuntu successfully but then thought I'd be smart and install mdadm and then break dmraid.  Bad idea.  I've reverted back to installing dmraid and commenting out the "dmraidtomdadm.cfg" file's kernel command line used by grub2.

There's actually an internet memo floating around about how mdadm isn't properly installed by Ubuntu as it requires IT Administrator like skills to change /dev/mapper/names and /etc/fstab entries for UUID's of RAID's instead of linux ext4 partition.  It's here if you are interested:[https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038095.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038095.html)

Being a sucker for punishment I want to setup caching instead of copying /boot and / (root) to the SSD's free data volume.  I've already partitioned it (just last night in fact using Window's DISKPART utility in Dos shell) and am reviewing the various options.  Again people are saying don't use dm-cache because it's outdated use flashcache instead because facebook uses it.  Then they say don't use flashcache but rather enhanceio because it's easier.  Then I read flashcache is based on dm-cache code and enhanceio is based on flashcache code.  Indeed dm-cache was just added to the kernel in 2012 or 2013.

I may have got my dm-cache versus dmraid kernel injections mixed up but you get my drift how free internet advice can lead you down the wrong rabbit hole.

For the laptop which has two hdd drive bays, plus a mSATA (think baby SSD) bay the fake raid solution works wonderfully. The factory mSATA is 32gb so 18gb is used to accelerate Windows 7 programs and data (boot goes from 45 seconds to 15 seconds and everything is FASTER.  12 gb is set aside for LINUX which gets me back to my caching project there.

 I was reading last night that TRIM is supported but have not thought that far ahead yet.

After this project is finished I think I'll pickup a 128GB or 256GB mSATA plus one or two 1TB SATA III HDD's (60 bucks each on sale).  Intel's fake RAID allows a maximum of 64 GB for accelerating Windows so there would be lots of room for of LINUX.

Although time-consuming and at times frustrating it's been a very educational project so far.  :)

---

### Post by carl33 on 2015-03-31
Hello guys,

I found this thread while searching for a solution to a very, very similar issue I am currently experiencing.
I will go into as much detail as possible, and any help is appreciated.

I have a Asus Maximus Hero VI z87 motherboard with i7-4770k
I setup a RAID 0 array with 2 120Gb SSD's as member drives using the motherboard's RAID configuration. (All pretty standard stuff)
I have Windows 7 Enterprise 64bit installed to this RAID volume.

I decided I wanted to dual-boot Ubuntu and Windows 7 because I want to start "transitioning" to Linux to eventually use it as my daily driver.
I went about this the same way I would in any other dual boot situation. I downloaded the most recent supported stable release of Ubuntu (14.04.2-Desktop-AMD64) and created a bootable USB using unetbootin from Windows.
I then booted the PC from the USB and Selected "Try Ubuntu without installing" so I could check things out. I am always cautious when messing with dual boot.
The Live Ubuntu desktop loads just fine and I am able to do everything I would expect.
When I launch the Install Ubuntu option, the Windows install is not detected. The Disks app does show 2 120Gb SSD's and that they are RAID disks, however it shows as 2 separate volumes instead of one.
I am familiar enough with Linux to use Terminal for some basic stuff (like using apt-get to download updates and apps, or adding repositories) but I get a tad uncomfortable past that. ALTHOUGH I am willing to try things and learn of course.
I say thins because the option I was looking for was the "Install alongside Windows 7" option. Since no Windos install is detected this option does not appear, and the RAID volume does not appear in the Install options as an available disk - it doesn't show either one of the SSD's.
At this point I thought that perhaps I needed to shrink the Windows partition leaving unallocated free space for the Ubuntu install. So I re-booted into Windows and did just that. I was able to free about 100Gb of space.
At this point just to try something else different, and because I like Gnome better than Unity I downloaded the Gnome 14.04.2 AMD64 iso and re-created the USB drive.
I then performed all the same steps as above. Once again at the install point, Windows was still not detected and the drives(RAID volume) was not available as an option.
I have seen a lot of stuff about mdadm and dmraid, and I learned that the Intel chipset RAID solution is not a TRUE RAID.

At this point I can always install Ubuntu to a seconday mechanical drive, but I really wanted to see what the performance would be like off my SSD raid.
Messing with the Windows install any further at this point is not an option, and I do not want to risk loosing any data. (Yes I do have everything backed up in 2 different location thanks to a nightly differential backup)

Is it possible to make this work the way I want to or am I out of luck? What would you all recommend?

Thanks in advance.

Carl

---

### Post by SkOrPn on 2015-03-31
I had exactly the same problem as you with my Intel ports. However I found an even better work around that has made me very happy to dual boot with the added bonus that Ubuntu does not see my Intel/Microsoft OS drives, and Windows does not see my Marvel/Ubuntu drives (I have no clue how this worked like this, but it works brilliantly on my board). However, what I'm about to suggest is probably not what your going to want to do and it assumes the ASMedia on your board can be put into RAID, which I doubt.

On your Motherboard you have an ASMedia chipset ASM1061 I think it is. In the BIOS it only shows AHCI and IDE, enable it and put it to AHCI. Then attach TWO identical drives (I used some old retired Vertex's I had lying around) to those ports and boot and see if your board has a screen that shows the drives on the ASmedia ports? If so, if it says something like "Ctrl + A" or something along those lines go inside and see if it it can be put into RAID mode. My Asus board has a Marvell controller "Ctrl + M" and inside the configuration settings it had RAID Stripe mode. Looking online it looks like your ASmedia does not do raid but I could be wrong. If it does do RAID, then you could use F8 every time you boot (bypassing any problems with Grub or BCD) and use the BIOS/UEFI to select your boot drive/OS. Again, this has worked brilliantly for me.

That is what I had to do because Ubuntu refuses to see anything on my Intel ports, even in RAID mode as a single drive to install to. However, Ubuntu instantly saw my two raided drives on the Marvel ports as a single storage device, so NOTHING to set up before hand. I'm using Ubuntu MATE 14.10 and just upgraded to 15.04 B2. Again it works fantastic, albeit not as fast as it would have been on the Intel ports though but that's OK.

Or maybe 14.04 wasn't ready for Intel fake raid out of the box?

By the way a few things I should mention. I use Parted Magic and had the Vertex's both wiped/cleaned before creating the array. So maybe Ubuntu wants to see perfectly clean non-partitioned drives first? Also, I did not try 14.10 on the Intel ports because I am testing Windows 10 as well and did not want to mess with that setup. My last try with Ubuntu and the Intel ports were at least 1 year ago using 14.04, and as you, Ubuntu only saw individual drives back then. So it could either be that Ubuntu 14.10+ now see's fake raid as single drives out-of-the-box, or there is something wrong with Intel fake raid. Again, my Marvel chipset is working perfectly for 14.10+

---

### Post by carl33 on 2015-03-31
Thank you so much for responding so quickly. I have been hitting up a few forums throughout the day and this is the first response I have received.
The Marvell controller on my board in fact does not have RAID functionality, but I am willing to settle without the raid for now. I have some WD 750Gb Enterprise drives sitting around and I  may just use one of those. I will grab 14.10 and try it out first just to see if it detects or not. Thanks again for the info.

---

### Post by SkOrPn on 2015-03-31
> **carl33 said:**
> Thank you so much for responding so quickly. I have been hitting up a few forums throughout the day and this is the first response I have received.
The Marvell controller on my board in fact does not have RAID functionality, but I am willing to settle without the raid for now. I have some WD 750Gb Enterprise drives sitting around and I  may just use one of those. I will grab 14.10 and try it out first just to see if it detects or not. Thanks again for the info.
Well don't thank me lol. I'm a novice when it comes to Linux and I been messing with it since the 90's. This is the very first time I have ever gotten Ubuntu to work in RAID before, so I kinda feel like it is 14.10 that made the difference for me and a miracle almost, haha. I just thought I would share the info even though it really does you no good. Oh and yes, using that second controller on your board does allow you to install Ubuntu to it in AHCI. That way you can keep windows on the RAID array and Ubuntu in AHCI. Set the BIOS to automatically boot the Intel raid array by default, and when you want to use Ubuntu just hit F8 and select your HDD that Ubuntu is installed to. Once you get proficient in Ubuntu, maybe down the road you can figure out how to get both on the same raided drives.

 Now all I have to do is hope that the next LTS release will allow me to upgrade to it.

---

