---
title: "repartitioning with Vista?"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by rozojc on 2007-03-17
Hi,

I just got myself a new laptop which comes with Windows Vi$ta installed in it. Thing is I do need to keep windows because of some software they use at my workplace, but in order to install ubuntu, I was thinking of shrinking the windows partition in order to have space for the ubuntu install. I read someplace that the NTFS system that Vista uses is different, and that because of that it is not possible to shrink the partition without basically screwing up the install... is this true? Could I shrink the partition (be it through the install of ubuntu or Partition magic) and install ubuntu without problems?

Also, if that is possible, will ubuntu screw up the boot, or will double boot work fine? I ask this because I've also read that Vista doesn't eally work with double booting well..

---

### Post by bulldog on 2007-03-17
Well you did some reading,that's always a good thing :) 

But to know if the things you want are possible on **your** machine,the only way is to try.
Nobody on this forum give you any guarantee it will work flawless,you can read success story's and horror story's,but if it will work out for you,you have to find out by yourself.

If you ran into trouble I'm sure there are people here willing to help you out,but we can't do anything more.

---

### Post by Toufik on 2007-03-17
Hi,

I've just buy a new laptop with windows on it.  After Vista installation, I install Ubuntu so I resize the partition.  Edgy works great afterwards, but I wasn't able to access the windows partition.  To check what happened, I reboot to Vista ... which show me the first installation screen  asking me for installation:( This time I check to repartition my disk at first.  Nope, Vista wants the whole hard disk, even when choosing two partitions!!  Nevertheless, I choose to repartition in two paritions, but then I get an error message and the installer quit.

Conclusion: my laptop doesn't boot anymore because grub is still installed but my linux partitions were destroyed by Vista. (grub error 17)

I don't know what to do!!!

For the moment, I'm reinstalling ubuntu to have at least something ...  But I'd like to reinstall Vista afterwards.  Therefore, I'm looking for some advice/help.

Thanks

---

### Post by mooseydoom on 2007-03-18
I'm dual booting Vista/Ubuntu right now, so it is possible.  [Here]("http://apcmag.com/node/5162/")'s a guide I found on dual-booting

My slightly convoluted story:
The first time I booted my laptop Vista was installing, but I thought it hung up so I rebooted the laptop in the middle of the installation.  Vista got stuck and wouldn't finish installing.  So I installed Ubuntu, and used the Ubuntu installation to shrink the ntfs partition that Vista was on.  Then I had to run chkdsk on the ntfs partitions because they aparently didn't like being resized by Ubuntu.  I used grub to boot the sony "hidden" system restore partition and use the restore c drive option to reinstall Vista.  Now can boot into Vista or Ubuntu.  :)

---

### Post by Toufik on 2007-03-19
I solves my problem by doing this (remember that my booting was stuck, see my post hereabove) :

* Download and burn a bootable Grub cd-rom ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) 
* Chose to boot on the first partition --> Vista format the hard drive. **_Choose two partitions_**, the D: will be for Ubuntu
* After that, reboot on the first partition --> Reinstalation of C:
* At the reboot, choose first to **activate** the second partition
* Then boot on the second partition --> Vista finishes his installation
* Reboot with a Ubuntu LiveCD, delete the last partition (your D: under Vista) and create new partitions (one primary for / (needs to be primary to be bootable), one extended (because maximum of 4 primaries) wherein you'll create one logical for /home and another logical for SWAP)
* This will also reinstall grub and now my computer is able to boot on his own to Vista or Ubuntu :D

---

### Post by mouseboyx on 2007-03-20
I just tried this yesterday (monday, march 19) and you must absolutly backup everything.
when i tried to shrink the partion it did not boot it just stayes at the stupid scrolling bar thing forever and im almost sure that the partioning was the problem i still cant get anything to work because i have no vista intall cd i want to just wipe my hard drive and install window$ xp but i cant.

when i get to the screen when im supposed to choose where to install it i think because i have like a gazilion little digital cammera memory stick drives and it doesnt even recognize my hard drive anywhere. (exept Ubuntu)

---

### Post by silverglade00 on 2007-03-20
Here is how I did it without any problems:

1. Boot up Vista. Let it take the hour or so to setup and configure itself. Make a sandwich, watch some TV. Just let it do its thing.

2. Right click Computer. Choose Manage. Go to Disk Management. Find your Vista partition (the big one) and right-click it. There is an option to shrink. Choose it.

3. In the resulting box, read the captions carefully. It's not asking how big do you want to make Vista's partition or the new partition, it's asking how much you want to shrink it by. Enter the amount of **MB** you want to reserve for Linux. Click on OK. This uses a lot of time.

4. When it is done, reboot to your Ubuntu CD. Create your partitions and install with the installer.

5. Enjoy! This will also use a lot of time :)

---

