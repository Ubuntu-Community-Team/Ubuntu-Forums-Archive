---
title: "URGENT HELP on Dual Booting Windows 7 and Ubuntu 12.04"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by anime4eva on 2012-09-03
Hi all,

I am new with Ubuntu but I like it after using it in my workplace so I want to dual boot in my new laptop, however, I took quite a lot of time to search for the instruction and it varies in different website so I guess posting it here is the best choice for me at this point of time. Thank you in advances for your help!

I will use Windows 7 for gaming and Windows-only application while all others will be done on Ubuntu.


Although as I understand that anything from INTEL will be supported easily by Ubuntu, however, still would like to double check whether my laptop can used for Ubuntu.

My laptop is Lenovo Y480 and its spec as below:

Intel® Core™ i7 Processor 3610QM
Nvidia GeForce GT650M 2G
Broadcom 802.11n Network Adapter
Atheros AR8161/8165 PCI-E Gigabit Ethernet Controller (NDIS 6.20)
Broadcom Bluetooth 4.0 USB

IS there any major devices that I did not mentioned above that will stop me from using Ubuntu?



OK if my laptop is good to install with Ubuntu, my plan to install is:

1. Overcome my 4 primary partition (Boot, Windows, Lenovo, OEM partition)
I plan to use windows back up and recovery to back up and burn into recovery disc. [I wonder does windows back up back up everything in C drive including the driver installed? Can I also change the partition size during the recovery process?]

After that, use the recovery disc to resize my partition into 150GB for windows and then install Ubuntu.


2. I saw a lot of instructions talking about primary, logical and extended partition. Is there any different between them?
I plan to put like this:
swap 8GB
/    40GB
/home 20GB
/shared 280GB

As you can see it is more than 4 partitions, can I put all of them under extended partition? /home will be stored personal information so I wonder is it better to combine with /

In addition, do I need to put in /temp? OR I missed out any important partition? Would really appreciate advises!


For software, I will refer to [http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin](http://www.howtoforge.com/the-perfect-desktop-ubuntu-12.04-lts-precise-pangolin)

Is there anything missing besides these software?


Lastly, in term of security, if i allows windows 7 to read and write on /shared will it create loophole for virus/hacker/malware?

Do i need to install anything else like on-the-fly encryption to ensure both windows and ubuntu are encrypted?

I understand that for MAC if some setting is done with the installation disc, the laptop cannot be reformat without the same disc which is great in the cases of being stolen. I wonder is there anything can be done for Ubuntu or Windows 7 as well?

I know it is a long questions, but really appreciate to have your help so I can start using Ubuntu asap!

THANKS

---

### Post by oldfred on 2012-09-04
I do not know about encryption. You can encrypt /home as part of the install of Ubuntu, but I do not know if Truecrypt or other encryption will work well with both Windows  & Ubuntu for your shared NTFS partition.

I do not know specifics of your hardware. From liveCD or USB run the live mode and try to see if everything works. USB is a bit faster and installs a bit faster.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

The extended partition is one of the primary partitions. You can only have one extended, but it can hold many logical partitions. Windows will read data (even a second install will boot) from a logical NTFS partition. Windows will not read Linux partitions but Ubuntu will read & write NTFS just find. But Windows system partition often does not like too much writing into it from foreign systems so use the shared data as read/write and set the Windows system partition as read only.

If you are going to put all or almost all data into your shared NTFS data partition you may not need a separate partition for /home. I use 25GB for / (root) including /home and use about 9GB. My /home is 2GB and most of that is .wine for Picasa. But I am aggressive in moving data to my two shared data partitions, one NTFS and the other Linux formatted.

If you have 8GB of RAM, you probably do not need 8GB of swap. That is suggested if you want to hibernate, but dual booting and hibernating often cause issues. And Ubuntu boots pretty fast so hibernation does not buy much.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Are you using both Intel & nVidia graphics. For the install you need to choose one. With nVidia you need the nomodeset boot parameter to get it to work until you install the nVidia graphics.

Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by 2F4U on 2012-09-04
> I understand that for MAC if some setting is done with the installation  disc, the laptop cannot be reformat without the same disc which is great  in the cases of being stolen. I wonder is there anything can be done  for Ubuntu or Windows 7 as well?

That would be totally new to me. Can you provide the source? Usually, encryption prevents an attacker from reading the content of your hdd, because that is protected. It does not prevent a person to install another system, unless you take measures to prevent anyone from booting from anything else than the hdd.

---

### Post by anime4eva on 2012-09-04
Thank you very much for your replies!

So basically I can combine / and /home into 40GB.

I can put all my Ubuntu under extended partition right?

If I not mistaken it is called firmware password or something for MAC




FINALLY

I done with my dual boot but having problem with the booting part as BIOS auto boot into Windows 7.

It is easy to install Ubuntu. For those with OEM partition, kindly reformat into factory setting and update the system into latest [remember to defrag them too; each actions should be accompany with restart x 2]. After that, search 'create system recovery disc' and 'back up'. Use these two options to back up your system into CD or other HDD.

Next, resize your system into the size you want via disk management [if your system disallow you to resize till the size that you want, just resize it to the allowed size and the reformat into factory setting again. As windows 7 system files tend to install in the mid of the drive, when the size grows smaller, it will install in other places too! so it enable you to resize to the size that you want!]

Reboot using Ubuntu CD/Live/USB and then press TRY Ubuntu. Search for GParted and use it. Delete the OEM partition and put all into Extended partition and save action. Then install Ubuntu and line up your partition accordingly.

/boot 1 GB
/         40 GB
/swap 8GB
/shared

Also remember to put boot system into /boot instead.

Everything should be fine as I done the steps too. Hope it helps for others who want to dual boot Windows 7 and Ubuntu 12.04!

---

