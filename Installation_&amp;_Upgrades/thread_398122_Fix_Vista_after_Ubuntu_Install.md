---
title: "Fix Vista after Ubuntu Install"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by bgeer on 2007-03-31
I used Ubuntu Edgy live CD to repartition & install on my Windows Vista laptop.  Naturally I didn't bother to do any research, just figured it would work ok...:-)

A month later, I wanted to demonstrate Vista & it refused to boot. THEN I researched the issue & found there are known Vista repartition issues.  Thanks MicroQuack!!!

If you find your Vista's not happy after repartitioning using Ubuntu repartitioner, run don't walk over to [www.linux-ntfs.org](www.linux-ntfs.org) & grab a cvs snapshot of their ntfs tools, specifically ntfsfix.  I executed "ntfsfix /dev/sda2" which took very few seconds then rebooted & selected Vista.  Vista did a little complaining then bashed away at the disk for a little while, & finally booted & ran.  I immediately rebooted Ubuntu to make sure it is still ok, & it is!

After downloading the cvs snapshot, simply
  tar jxvf ntfsprogs_[date]_.tar.bz2
  ./configure
  make
  sudo make install
& run ntfsfix [vista partition device name].

From the linux-ntfs faq:

"Ntfsresize Frequently Asked Questions
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#vista](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#vista)

Question: Does ntfsresize support Windows Vista NTFS?

Answer: Yes but only ntfsresize version 1.13.1.1 and later. Resizing Vista
partitions with earlier versions make Vista unbootable but the problem
doesn't affect any user data.

The unbootability can be fixed by resizing NTFS again with at least
ntfsresize version 1.13.1.1, or running the latest version of ntfsfix or
ntfsresize from the ntfsprogs CVS, or by running non-Vista chkdsk on the
partition.

The problem is caused due to Vista believing that the volume was mounted by
NT4 last time which is not supported by Microsoft anymore, so it refuses to
boot.

Please also note that GParted is well-known to damage the partition table
sometimes (especially the version included in Ubuntu) and that problem is
completely unrelated to NTFS. E.g. if no NTFS signature is found on the
partition then that's definitely points to a partition table
corruption."

HTH, Bob

---

### Post by razorfrog on 2007-04-01
Hi Bob-
I have this same problem, and this looks like the first real response. As this is my first linux adventure, and I'm still figuring out how to do things. Can you post a more complete walkthrough for running the fix utility? I have the files downloaded and un-tarred, but I cannot run the utility. Please help!

Thanks!

---

### Post by razorfrog on 2007-04-01
Alright, I figured out the install.. Problem is, the ntfsfix comes up with:

Mounting volume... Error opening partition device: Permission denied
Failed to startup volume: Permission denied
FAILED
Attempting to correct errors... Error opening partition device: Permission denied
FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

Now what?

---

### Post by razorfrog on 2007-04-01
ah ha! this totally worked. 
i'm dumb and forgot to sudo the ntfsfix

thanks!

---

### Post by bgeer on 2007-04-01
I wasn't logged in to see your question...as with most things Linux, perseverence will solve the problem.  Glad it worked for you.

Cheers, Bob

---

### Post by dellUsional on 2007-04-01
I searched linux-ntfs.org but came up empty. It seems like the cvs snapshot and/or ntfstools is no longer available from that site. Any work arounds? Thanks.

---

### Post by razorfrog on 2007-04-01
it's all still there.  try:
[http://data.linux-ntfs.org/cvs-snapshots/ntfsprogs-200702071432.tar.bz2]("http://data.linux-ntfs.org/cvs-snapshots/ntfsprogs-200702071432.tar.bz2")

---

### Post by dellUsional on 2007-04-01
thanks. got the file and attempted to compile it. the resulting error is...

[INDENT]configure: error: C compiler cannot create executables
See `config.log' for more details.
[/INDENT]

I viewed config.log using "more config.log" but it's totally 'over my head.' where do I go from here?

---

### Post by confused57 on 2007-04-01
> **dellUsional said:**
> thanks. got the file and attempted to compile it. the resulting error is...

[INDENT]configure: error: C compiler cannot create executables
See `config.log' for more details.
[/INDENT]

I viewed config.log using "more config.log" but it's totally 'over my head.' where do I go from here?
You probably need to install build-essential, open Synaptic Package Manager & do a search for it.
See this link for installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
it's toward the bottom of the page

---

### Post by dellUsional on 2007-04-03
OK, I installed build-essentials.
Then I CD'd to the ntfxprogs directory and ran...

./configure
make
sudo make install

that seemed to go alright, but when I try...

sudo ntfsfix /dev/sda1

I get this...

[INDENT]Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Volume is corrupt. You should run chkdsk.[/INDENT]

I'm not sure about the volume info of my Vista partition. I installed Vista first. So is it /dev/sda1 or /dev/sda0? Or what?

I know that the system linux partition is /dev/sda2.

How can I see the ntfs partition in ubuntu? Thanks.

---

### Post by dellUsional on 2007-04-03
Oh hell, I didn't really "fix" it, but I got it working.

Re-installed Vista...
Installed easyBCD (don't know if I still need though it is a good precautionary tool)...
Deleted Linux partitions...
Re-installed Ubuntu using all available disk space (ie. no resizing them thangs)...

Now the Grub loader has an option at the bottom which says...

Alternate OS:
Vista (Longhorn)

I will tread gently and edit the grub file. Longhorn? WTF?

---

### Post by denysy1 on 2007-04-06
> **bgeer said:**
> 

After downloading the cvs snapshot, simply
  tar jxvf ntfsprogs_[date]_.tar.bz2
  ./configure
  make
  sudo make install
& run ntfsfix [vista partition device name].


HTH, Bob

Could you please give an example of how your ntfsfix command looked like?

---

### Post by destructiveproperty on 2007-04-11
I'm new to linux and trying to learn as much as I can, could someone post a screenie on how to do it, I can't get it work work, I just don't think I'm putting in the script right, but I'm not sure

---

### Post by Computer Guru on 2007-04-13
Well, if you are using EasyBCD, here's the [step-by-step documentation]("http://neosmart.net/wiki/display/EBCD/Linux"), and even better, a step-by-step guide [with screenshots and pictures]("http://apcmag.com/node/5162/") the whole way through.

---

### Post by Atlae on 2007-06-07
Hey all,

I'm exactly where DellUsional was in the process, and getting the exact same error message.  I'm pretty sure that the partition for Vista on my computer is /dev/sda2, but when I type

sudo ntfsfix /dev/sda2

I get the error message:

Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Volume is corrupt. You should run chkdsk.

Any ideas?  I'm not ready to reformat my hard drive / reinstall Vista just yet.

---

### Post by stil on 2007-06-23
Hi. I thought it would be ok to bump this thread instead of starting a new one.

I've had the same problems with Vista booting to a point then stopping. I have installed ntfsprogs and attempted to run ntfsfix.

ntfsxfix /dev/sda1 

I get this message...

"Refusing to operate on read-write mounted device /dev/sda1"

I'm running the command as root. Not sure where to go from here.

---

### Post by merlinus on 2007-06-23
You might try unmounting the drive.

-merlin

---

### Post by stil on 2007-06-23
That worked, thanks for tolerating my ignorance :confused: Early days for me still.

---

### Post by stil on 2007-06-23
Great, vista boots up properly! But it now can't shut down #-o

*shakes fist in the air*

Could be be something to do with vista having to write to its MBR while shutting down?

---

### Post by marcus_brutus on 2007-06-24
hi 
i have acer aspire 5610 laptop.i installed ubuntu 6.06 and i did perform the ntfs fix thng but still the same ..... the grub shows windows nt/2000/xp instead of vista and on selecting.....the windows XP screen comes first and then  the acer recovery starts wich sks me to restore system to factory settings.....
wha should i do pls help

---

### Post by stil on 2007-06-24
Hi.

You say it lists 2000 etc instead of vista. And then you see an XP screen. Do you have vista and XP installed?

Can you post the contents of menu.lst?

---

### Post by amuzo on 2007-06-30
to view volume information:
#sudo ntfsinfo /dev/sda1 -m

if the volume is mounted:
#sudo ntfsinfo /dev/sda1 -f -m

to run ntfsfix in first partition of windows, maybe:
#sudo ntfsfix /dev/sda1

good luck!
amuzo
[http://amuzo.net](http://amuzo.net)

---

### Post by ndinadis on 2007-07-05
So I am having the same problem as others in this thread have, I have tried using ntfsfix without success,  Vista goes to boot up shows the progress bar then reboots I have tried the fix twice and it has said it has fixed successfully it still does not work though.
I really need to be able to access vista again!
Thanks, Nick

---

### Post by Joe23 on 2007-11-04
Just a quick note to say that you can also get round this problem by booting from the Vista DVD and click "Repair this computer".

You will get a prompt saying it detected startup problems with your installation and offers to repair them.

Once your system has rebooted, select your Vista installation from the bootloader, Windows will then perform a chkdsk and reboot.

Now you can boot between Ubuntu and Vista without any more problems!

---

### Post by daninchina on 2007-11-08
I seem to be having the same difficulties as other people on this thread.

I'm running Ubuntu 7.10 on a Lenovo/IBM Thinkpad T61. It's my company's machine but I decided to put Ubuntu on as well and dual-boot.

Unfortunately, I've been trying some of the fixes above and nothing has worked yet.

It should be noted that now Ubuntu is not reading the ntfs vista partition at all now (it did intitially after the install, but after a few reboots and hard resets later, it is not happy.

After doing some research, I think this can be chalked up to using a Gparted cd to handle the Vista partition resizing...apparently that is a no-no.

Hopefully my IT manager has a restore disc that will let me repair the windows partition without totally needing to reinstall.

I have tried: 

1. Installing ntfstools. Installation went well, but it is not helping me when my system isn't seeing any ntfs partitions at all.

2. Running a windows vista install cd to attempt a repair. The laptop read and read the cd, and after it loaded, all I saw was a blank screen.

I'm not sure what to do next. I will burn a copy of Supergrub shortly and see what I can do with that.

Any other suggestions?

---

### Post by kurotsuno on 2007-11-08
Is it worth dual booting then ? all of what I've read seems to lead to Vista having big problems I was thinking of installing ubuntu as a second operating system but reading this stuff really makes me somewhat reluctant.

---

### Post by maniqui on 2008-02-13
Hi all. This is a happy ending story I will share with you just to keep a record of this issue.
This thread (and a Xubuntu Live CD, of course) helped to fix a problem after repartitioning a HDD that has Vista installed on it.

Some weeks ago I helped a friend (well, a friend of my mom) to buy a laptop. She chose a Toshiba with Vista pre-installed.
My job was to prepare (tune & tweak the system, install programs, etc) the laptop so she has her e-mail, MS Office, and all the data from her old HDD.

I really didn't want to wipe-out the whole HDD of the new laptop and re-install the system, because I wanted to do my job as fast (and as good) as possible. 
So, first step, to partition the 160GB HDD to have at least two partition: one for the system, and the other one for documents.

So i booted with a GParted Live CD to do the job. Ah... how much I hate laptop manufacturers when they do their own non-standard-way of partitioning. There were unallocated space at the beginning of the HDD, then a 2GB partition labeled something like "Toshiba System" (i can't remember), then the Vista partition (a huge one), and finally some more unallocated space.

As said, i wanted to finish my job ASAP, so I decided to leave untouched the unallocated space and the "Toshiba System" partition, and just shrink the Vista partition and then create a new large partition following that one.
So, I did it, it took like 2 hours to finish.

After that, Vista won't boot. It will just display the green loading bar and then, a black screen. And then nothing.
I started to think that i will going to need to reinstall everything using those Toshiba Rescue Disks (two DVDs) and start from the beginning, and spend more time... I started to sweat...

So I connected my own laptop to Internet and started to search for this issue. As always, you have to be a very bad luck guy to be the first one to suffer a technical problem.
So, googling during a few minutes and finding similar problems, I arrived to this thread at Ubuntu forums.

So I grabbed (and kissed) my Xubuntu installation disc and boot with it as a LiveCD.

As suggested on the thread, I executed the following at a terminal:
```
ntfsfix /dev/sda1
``` (where "sda1" is the Vista partition)

The command reported that something was fixed... so I rebooted to see what happens!
And as i said, this is a happy ending story: Vista booted and so I continued tuning, tweaking, and installing programs...
:D

Hope this helps someone out there.
Thanks to the starter of this thread for sharing his knowledge.
Thanks MS again for making things that don't work.

---

### Post by ndinadis on 2008-02-13
Just so you and others know, vista has its own formating utility built in, it works quite well, and as you found it does not like being partitioned any other way, it has something to do with the way the files are arranged in vista compared to XP, linux and everything else.

---

### Post by maniqui on 2008-02-13
^ ^ thanks, ndinadis. Good to know that Vista has its own partitioning tool. I didn't know that (or if I did, I totally forgot about it).

Although, I feel more confident using a tool like GParted or any other partitioning tool that works **outside** the OS (well, I don't know this, but probably the Vista partitioning tool sets a batch/cron job that will run after rebooting the machine).

---

### Post by ndinadis on 2008-02-13
the vista partition tool works well, I have used it to partition out space to use for dual booting ubuntu which resulted in having vista not boot :( 
I have had vista installed on its own for a while now and just got a virus or some spy ware yesterday that has propeted me to go back to something that works and is safe from those problems (linux)
Had anyone had any luck trying to get the two working on a dual boot?

---

