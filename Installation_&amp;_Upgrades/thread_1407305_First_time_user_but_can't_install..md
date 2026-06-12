---
title: "First time user but can't install."
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by urepedese on 2010-02-15
I am trying to install Ubuntu onto a computer that I have just assembled. I want to dual boot and have installed windows. I purchased my Ubuntu CD which is verson 8.004.  It will not install however and I get a black screen that ends with 'initramfs'. When I try to install text only it firstly does not recognise the network adapter, and secondly it won't recognise the hard drive. From this point I can't proceed.

Luckily the Asus Motherboard came with this Express Gate linux application:)

Any help would be appreciated.

Jason

---

### Post by saif_held on 2010-02-15
Did LiveCD work?

---

### Post by zeroseven0183 on 2010-02-15
> **saif_held said:**
> Did LiveCD work?

Be sure to set the computer to boot first from optical drive. This can be set in the BIOS.

---

### Post by urepedese on 2010-02-16
Yes the Live CD works. I will post the full text on anther post. Right now I just want to test this as I have had trouble trying to post.

---

### Post by urepedese on 2010-02-16
I get further in 'text only' install, but it will not detect the hard drive (WD6400AALS) and therefore will not proceed past the partitioning.

Full text I get for normal install is:
udevd-event[1687]: run_program: '/sbin/modprobe'abnormal exit.
Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs)

Specs on my machine are:
i5-750, asus p7p55d e pro, 2x2Gb super talent ram, corsair HX650, XFX gtx260, and hard drives as above. OS already installed is XP Home Edition.

---

### Post by jocko on 2010-02-16
> **urepedese said:**
> I purchased my Ubuntu CD which is verson [COLOR=Red]8.004[/COLOR].
I'm sure you mean 8.04.
Since the ubuntu version you are trying to install is much older than the hardware you are trying to install on chances are that some of the hardware in your motherboard is not supported by the kernel in 8.04 (8.04 was released in april '08, but your cpu didn't exist until September '09 and according to asus' home page the first bios for your motherboard was released in November '09).

Try to get your hands on the current ubuntu release instead (9.10, released in October '09). It is much more likely to support your machine.

---

### Post by urepedese on 2010-02-17
> **jocko said:**
> I'm sure you mean 8.04.
Since the ubuntu version you are trying to install is much older than the hardware you are trying to install on chances are that some of the hardware in your motherboard is not supported by the kernel in 8.04 (8.04 was released in april '08, but your cpu didn't exist until September '09 and according to asus' home page the first bios for your motherboard was released in November '09).

Try to get your hands on the current ubuntu release instead (9.10, released in October '09). It is much more likely to support your machine.

Mate thanks for that. I did suspect that this was the case. I didn' realise 8.04 was so old! I actually have a 9.04 iso image already downloaded so hopefully I will be okay. I have heard that Mint Gloria is also a worthwhile alternative to Ubuntu, would you recommend that and is that more likely to support my MOBO?

---

### Post by pbpersson on 2010-02-17
> **urepedese said:**
> Mate thanks for that. I did suspect that this was the case. I didn' realise 8.04 was so old! I actually have a 9.04 iso image already downloaded so hopefully I will be okay. I have heard that Mint Gloria is also a worthwhile alternative to Ubuntu, would you recommend that and is that more likely to support my MOBO?

The current Mint release is 8 (Helena) which is basically the same as Ubuntu 9.10

I am sure that Gloria is the same as Ubuntu 9.04 - what I mean is that the kernel is the same and the device support should be identical

---

### Post by MCVenom on 2010-02-17
Mint Helena ( 8 ) is better, and whether to go with Mint or Ubuntu is really up to personal preference. Personally, I use Mint 8 now but I'm going back to Ubuntu as soon as Lucid Lynx comes out, Mint is a bit too bloated for me :p

---

### Post by sailthesea on 2010-02-17
> **urepedese said:**
> Mate thanks for that. I did suspect that this was the case. I didn' realise 8.04 was so old! I actually have a 9.04 iso image already downloaded so hopefully I will be okay. I have heard that Mint Gloria is also a worthwhile alternative to Ubuntu, would you recommend that and is that more likely to support my MOBO?

 Both are good, the benefit of Mint is that you will have most media codecs and some other stuff ready installed But a few lines of code will do the job if you have Jaunty 9.04 handy
 See here
 
 [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by urepedese on 2010-02-18
Well I burnt off the Ubuntu 9.04 iso I had and it has loaded up okay on a separate laptop. I am now using it to post this.

Problem for me now is that I took the option to allow access to windows profiles and it didn't install like I had hoped. Windows has now taken up most of the install, not half as I instructed.

Result is that when I try to update anything I get a message saying there is no space.

I also can't open up Open Office.

I am assuming I need to do the install again, but when I try this from the disk it wants to keep the existing install on a partition. 

How do I uninstall/reinstall to get myself out of this one?

---

### Post by MCVenom on 2010-02-18
> **urepedese said:**
> Well I burnt off the Ubuntu 9.04 iso I had and it has loaded up okay on a separate laptop. I am now using it to post this.

Problem for me now is that I took the option to allow access to windows profiles and it didn't install like I had hoped. Windows has now taken up most of the install, not half as I instructed.

Result is that when I try to update anything I get a message saying there is no space.

I also can't open up Open Office.

I am assuming I need to do the install again, but when I try this from the disk it wants to keep the existing install on a partition. 

How do I uninstall/reinstall to get myself out of this one?
You can boot GParted from your Ubuntu LiveCD, and use it to format your current Ubuntu partition, and resize your Windows partition (BACK UP IMPORTANT FILES, JUST IN CASE). I'll look for tutorials for you and post whatever I find. After using GParted to format/resize your partitions you can reinstall Ubuntu on your formatted space.

---

### Post by MCVenom on 2010-02-18
Here's a tutorial on Gparted that covers all you need to know: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You can run GParted right from your Ubuntu LiveCD (it should be included on it), so you can ignore the step about making a special LiveCD for it, good luck! :D

---

### Post by urepedese on 2010-02-18
Okay thanks I will give that a go. It really helps to get links as it is really time consuming trying to browse through to find the right tutorial. Am trying do the drive image thing at the same time.Sigh.

---

### Post by urepedese on 2010-02-18
Okay I still don't really know what I am doing here.

I am showing four partitions. One is the windows nfts partition showing 90GB used on the 100GB drive, but 32 of those unallocated.

There are three other partitions, one and extended, an ext3 and a linux swap file. The extended and swap file have a little key window beside them and are locked.

I initially tried reduce the size of the windows nfts partition, but it says an error occurred during the operation.

---

### Post by darkod on 2010-02-18
> **urepedese said:**
> Okay I still don't really know what I am doing here.

I am showing four partitions. One is the windows nfts partition showing 90GB used on the 100GB drive, but 32 of those unallocated.

There are three other partitions, one and extended, an ext3 and a linux swap file. The extended and swap file have a little key window beside them and are locked.

I initially tried reduce the size of the windows nfts partition, but it says an error occurred during the operation.

1. What version of windows do you have?

2. Try to explain more precisely about the partitions or post a screenshot of Gparted. Like:

/dev/sda1, ntfs, 100GB, 90GB used
etc

I didn't really understand exactly what you have on partitions, how much space is used, and how big is the hdd in total.

---

### Post by MCVenom on 2010-02-18
> **urepedese said:**
> Okay I still don't really know what I am doing here.

I am showing four partitions. One is the windows nfts partition showing 90GB used on the 100GB drive, but 32 of those unallocated.

There are three other partitions, one and extended, an ext3 and a linux swap file. The extended and swap file have a little key window beside them and are locked.

I initially tried reduce the size of the windows nfts partition, but it says an error occurred during the operation.
I believe that if you right click the extended partition or one of the sub-partitions under it, it'll give you the option 'Toggle Swap'. Choose this and the extended partition will be unlocked. You can then format it as unallocated (this will erase all the data on your Ubuntu partition). Then you can reinstall Ubuntu, and the installer should provide an option to resize partitions.

---

### Post by darkod on 2010-02-18
> **BlackOtaku said:**
> I believe that if you right click the extended partition or one of the sub-partitions under it, it'll give you the option 'Toggle Swap'. Choose this and the extended partition will be unlocked. You can then format it as unallocated (this will erase all the data on your Ubuntu partition). Then you can reinstall Ubuntu, and the installer should provide an option to resize partitions.

The option is called Swapoff to be precise.
And you delete partitions to transform the space as unallocated, you can't format it as such.

But if you have windows vista or 7, they have a tool which is better to be used for shrinking the system partition because using the ubuntu installer can sometimes corrupt it. That's why tell us which version are you using and then we'll see.

---

### Post by urepedese on 2010-02-18
I am using XP Pro so looks like I will have to risk the Hard Drive. Nothing critical on it as I have copied all that off. I don't have the Pro disk however, but could probably source one eventually and I have the serial on the back of the computer.

I tried to image the drive yesterday using dd, but that said there wasn't enough room and I gave up before I got it sorted.

If this goes well at least I have figured out how to post a screen shot, if not can someone tell me how.

[IMG]http:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by darkod on 2010-02-18
Yes, for XP you have to use some program. In that case you might as well use Gparted from the LiveCD. But the main point is to shrink first (not as part of the install process), boot XP few times so it can figure out the new size of the partition and do its disk checks, and only then start the ubuntu install process. This minimizes the possibility XP to get corrupted.

You can take a screenshot in Applications-Accessories in ubuntu. Just make sure you set a delay for example 3sec, so the Take Screenshot window will close before the shot is actually taken. Otherwise it will be in the middle of your shot. :) You can do all this in live desktop too, and can even post here.

---

### Post by urepedese on 2010-02-18
[IMG]http:///home/ubuntu/Desktop/Screenshot-1.png[/IMG] I just used print screen and that seems to take a screen shot alright. I just don't know how to paste it in my message. I will attach it this time. I will also attach it as a jpg just in case.

---

### Post by darkod on 2010-02-18
> **urepedese said:**
> [IMG]http:///home/ubuntu/Desktop/Screenshot-1.png[/IMG] I just used print screen and that seems to take a screen shot alright. I just don't know how to paste it in my message. I will attach it this time. I will also attach it as a jpg just in case.

At the moment, do you get a grub menu at boot or your computer boots straight into XP?

---

### Post by urepedese on 2010-02-18
I was getting the grub menu. At least I know what a grub menu is now.Lol. But as you will see from my next screen shot I won't get it now. I hope I didn't use the delete button too soon. I was able to use firefox from the install, but I couldn't download the latest flashplayer update, or anything else for that matter. Should I now boot windows a few times and then reload 9.04.

Hey I have another issue here with my trying to image a drive using a Knoppix cd that I have mentioned. I am getting the same ' output file /dev/sdc1.img not enough space for operation' Can you guys point me in the right direction for that, or would I get help on these forums if I posted another thread about that?

When I do fdisk -l there does appeat to be enough space. The command I am using is 
'dd if=/dev/hdc1 of=/dev/sdc1.img'

---

### Post by darkod on 2010-02-18
It's OK that you deleted those partitions, but if you get a grub error now, because the ubuntu partition is deleted you need to do this:

Boot into live desktop again, in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore any warnings. That will install generic windows mbr on your hdd so that XP can boot now. Check if XP is booting.

Then again boot the ubuntu live desktop, open Gparted again and shrink /dev/sda1 for as much as you planned. Leave the space as unallocated. Click on the green button to execute that.

Reboot XP few times.

Boot with ubuntu cd again, Install Ubuntu option, and in step 4 tell the installer to Use Largest Available Free space.

And that should be it. :)

DON'T play with dd too much, that's a VERY dangerous command. Leave that for the time being.

---

### Post by urepedese on 2010-02-18
Okay thanks heaps, that looks like it will do the trick for me now.

The dd'ing is for an old IDE drive from my athlon xp2500+. It died on me last year and now that I have just built another computer (first build at 41 years:)) I bought an extra HDD for the old machine. So I have a new install on my new computer and it won't be a big deal if I lose anything, except for a few docutments and photos I want to recover from the IDE drive I am trying to image. So I am trying to image onto a drive with just one formatted partition of a 80Gb, to cover the 75Gb's or so on the IDE.

But back to ubuntu.....

---

### Post by darkod on 2010-02-18
You could try to use CloneZilla especially if you want to copy the whole partition. It also compresses so the resulting file should be about 1/3 of the data (according to them). It comes as bootable cd image on their website. You can boot with it and image a whole partition/disk, you don't even need to have working OS on the computer.

The only "bad" thing I don't like about it is that the restore has to be on a partition of the same size or larger, to guarantee successful restore. If you backed up 80GB partition which only had 40GB data, you can't restore to 60GB partition. It must be 80GB or more even though it only had 40GB data. That's from their FAQ in order for the restore to be guaranteed.

---

### Post by honey toast on 2010-02-18
Could it be that you did not shower yet?...or maybe you have not brushed your teeth and your gums? 
Try using deodorant and moth balls in your pockets.

---

### Post by urepedese on 2010-02-18
> **honey toast said:**
> Could it be that you did not shower yet?...or maybe you have not brushed your teeth and your gums? 
Try using deodorant and moth balls in your pockets.

I guess not, I will have to try those things.


 Well this is starting to do my head in. I am getting this when I use the apt-get command. And the second command says that it doesn't like -M.

---

### Post by urepedese on 2010-02-18
Okay have that last problem sorted and windows is now booting:)
# apt-get --reinstall install packagename did the trick.

---

### Post by urepedese on 2010-02-19
Success it appears! So thanks heaps for your help guys. It ended up that I managed to resize the windows partition after a defrag, althought that took 16 hrs!

I haven't yet checked the windows boot, but I am downloading 9.10 now. 

I do have a problem on my new machine, but will start a new thread for that one.

---

