---
title: "Installing Ubuntu Server 14.04 LTS on Proliant Microserver Gen8 G1610T?"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by johan23 on 2015-01-21
I have the following system:
- Proliant Microserver Gen8 G1610T
- 4 GB Kingston 1600 + out-of-box 2 GB memory (for a total of 6 GB)
- One 500 GB WD Black
- One 6 TB WD Red

I am completely new to both servers and Ubuntu. I bought this system to basically set up a plex media server. I chose Ubuntu Server 14.04 LTS mostly because it is free of charge but also because it seems stable once you get it configured and running properly. Figured all I had to do was to follow one of the online youtube videos... :)

I am trying to install Ubuntu Server 14.04 LTS on my system through a USB. The USB was created with PenDrive. I want the OS on my 500 GB disk and all media on my 6 TB disk.

I managed to boot the USB and get through all the steps in the installation program. After finishing the installation and rebooting, the system won't start Ubuntu. Instead I get the following messages in an endless boot loop: "Attempting boot from nic", "no boot filename received", "Non-system disk or disk error".

When attempting to boot from my USB, I get the error "No such device: 6566edfc-bbfc-4022-a5f6-c66449c1a333", and the system enters something called "rescue mode" and "grub rescue". No idea what this is.

When installing, I partitioned my 500 gb to: 6 GB "Swap", 44,1 GB "/" with EXT4 and 450 GB "/home" with EXT4. My 6 TB I partitioned to: 6 TB "homea" with EXT4. I might have forgotten to set the boot flag to "on" on my 44,1 GB "/" partition.

So... Basically I can not start Ubuntu, I can not re-install Ubuntu and the system doesn't seem to recoqnise USB:s anymore... Please help me solve this issue. At least I would like to be able to boot off the USB again and try re-installing everything.. 

Best regards

---

### Post by TheFu on 2015-01-21
Please post the URL created by the **boot-repair**  liveCD or **boot-info** scripts.
EFI or BIOS is important to know too.

---

### Post by johan23 on 2015-01-22
You will have to walk me through how to use boot-repair / boot-info scripts and EFI / BIOS scripts as I am a complete newbie to Ubuntu / Servers. I do not have a CD/DVD-reader in my server so everything needs to be executed through USB.

It seems that after installing and rebooting my 2 hard drives are no longer recoqnised by Ubuntu using the "ls" command in grub. I read that this might be a common problem for HP Proliant Microserver Gen8:s due to the B120i and lack of linux support. See link below.

[http://askubuntu.com/questions/524814/how-to-install-ubuntu-server-on-hp-proliant-microserver-gen8](http://askubuntu.com/questions/524814/how-to-install-ubuntu-server-on-hp-proliant-microserver-gen8)

I would of course like to run Ubuntu using the B120i as well. Also, the HP seems to have a fan issue which needs to be adressed with updated drivers. See link below. How do I practically install the OS along with these drivers and in what order? And how do I set up the driver-USB:s from a computer with Windows 7? Since I can't boot into the OS after installing, I guess the drivers need to be installed first? Ur during OS-installation? I need a newbie detailed step-by-step instruction I think... :)

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c04226727](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c04226727)

---

### Post by rumpelshtinski on 2015-02-24
Hi there, any luck with installing Ubuntu server? I plan to buy the same machine soon and plan to use it in much the same way as you do... But I am also a newbie in this whole server thing and I am worried that I will just waste my money on something I will not even be able to set-up in the end....

I found one page with a lot of useful links for G8 Microserver [http://homeservershow.com/forums/index.php?/topic/5639-proliant-microserver-gen8-links/](http://homeservershow.com/forums/index.php?/topic/5639-proliant-microserver-gen8-links/)

Maybe you will find it useful. Please do let me know if you succeeded and feel free to drop any useful tips ):P

---

### Post by MAFoElffen on 2015-02-25
Here;s your manuals:
[http://h20628.www2.hp.com/km-ext/kmcsdirect/emr_na-c00191707-18.pdf](http://h20628.www2.hp.com/km-ext/kmcsdirect/emr_na-c00191707-18.pdf)
[http://h20565.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=5379860&docId=emr_na-c03787037&docLocale=en_US](http://h20565.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=5379860&docId=emr_na-c03787037&docLocale=en_US)

There is a firmware fix for your controller that was released 2015.1.15, Unfortunately, that alone, will not help it with Linux. The B120i controller works with Windows servers with a software driver... For Linux, at least for RHEL, there is a driver, but only availabe from HP... See these Advisories:
[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c03742583](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c03742583)
[https://access.redhat.com/articles/118133](https://access.redhat.com/articles/118133)

I've converted rhel rpm packges over to Ubuntu... and HP has an Ubuntu Repo (more on that below), but consider the following first:
When I helped a company in Holland install an HP server with one of the B120i RAID cards, we ended up setting the drives to JBOD... and just using mdadm for Linux Software RAID. We found that the B120i is more like fake-RAID, in that it needs a software driver to work. It's not like true LSI Hard-RAID. With that in mind, it was an easy choice for them to go with mdadm. If it's going to need a software driver to work, then why not just use mdadm? They've been running production with theirs for over 2 years now, with no issues.

HP does have their own Proliant  Linux Ditro's repo, for their toolset. It does include Ubuntu and Debian. I was using that repo for one of my servers when I first set it up. But to be honest, I haven't looked through that repo recently.

*** Hopefully a mod will move this to the Server Section, so that this thread gets better exposure.

---

