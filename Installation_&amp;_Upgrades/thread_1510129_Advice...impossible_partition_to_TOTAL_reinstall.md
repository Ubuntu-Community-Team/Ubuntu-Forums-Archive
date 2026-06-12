---
title: "Advice...impossible partition to TOTAL reinstall"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by quirkification on 2010-06-15
So I have been using Ubuntu for a couple weeks now. And was not well informed in software before switching. And I have hit a wall it seems, on my Ubuntu partition I have it running and all my music(30+ GB) on my computer with GB free space. This makes me nervous, I don't expect to fill that space, but on a 320GB hard drive with an extra GB on the windows partition I am screwed. Plus I screwed up my first Ubuntu install...uninstalling a file for the network and was without the internet I needed to reinstall my mistake. So I have two Ubuntu and one works. I f***ed the first one up.

And I am missing useful space for Ubuntu. But I do have 10gb unallocated on my hd...

So I guess my question(s) is/are, I would love to NOT use windows, and I have my printer working; but not my 1gb apple shuffle (2nd gen) doesn't seem to work with linux.

Do I have to keep windows for iTunes, or should I 100% switch to Ubuntu, is there any reason to keep a windows boot?

Do I reinstall windows 7 and Ubuntu? I know that will fix my space problems, but take LOTS of time.

---

### Post by dino99 on 2010-06-15
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Arand on 2010-06-15
Those are decisions for you to take, depending on your preferences. We can't tell whether or not YOU need a windows boot. We can neither tell whether or not YOU have the time to do a complete reinstall.

Itunes works fairly flaky in Wine.
A few music players, including Rhythmbox should work with ipods.

If you would like some hints as to cleaning up partitions and re-allocating unused space, pasting some info like```
sudo fdisk -l
```or a screenchot from gparted will be useful.

- arand

---

### Post by quirkification on 2010-06-15
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc3/hs335.snc3/29384_437255558967_658848967_5780372_3883596_n.jpg[/IMG]

Well, I don't know where I had seen I had 10GB of space... But I do still feel claustrophobic here, I should have trusted that I would have loved Ubuntu so much.

Well...I do have the time to reinstall both systems...But I would much rather shrink the my windows partition.

I just have unmovable files limiting the shrink, currently I can move a whopping 445mb, is there any workaround for something like that and save the hours of reinstall.

And if I do reinstall, can I save my compiz settings to my Ubuntu One?

---

### Post by quirkification on 2010-06-15
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs344.ash1/29384_437291248967_658848967_5781240_5757370_n.jpg[/IMG]

And heres the terminal view.

If thats helps you, which I hope it does, still foreign to me.

---

### Post by Arand on 2010-06-15
1. To reclaim the ~15GiB you have at the end of the disc:
[LIST]
[*]Boot a liveCD
Use GParted: 
[*]Expand the extended partition to the end of the disk
[*]Expand the Ubuntu partition to fill the whole extended one
[/LIST]
You might want to consider adding a swap partition, unless you have reasons not to.

In order to get rid of unmovable files on the NTFS partition, I would suggest defragmenting the disk with something like MyDefrag (JKDefrag), which can take an option to "Force together" the data on the partition. like so:```
JkDefrag.exe -a 5 C:
```(run than in windows, it'll take an aeon or two).

The normal windows defragger might be able to do this, but likely much less effectively.

Then you should be free to shrink the NTFS and expand ubuntu also towards the beginning.


As for backing up compiz, if you have compizconfig-settings-manager installed, just go to preferences there and you should be able to export your compiz profile into a single file, which you can just save somewhere (USB stick, Ubuntu One...) and import again.

- arand

---

### Post by quirkification on 2010-06-15
cool running mydefrag now, lets catalog how long it takes. started 2 minutes ago. 4:02pm...

---

### Post by Arand on 2010-06-15
> **quirkification said:**
> cool running mydefrag now, lets catalog how long it takes. started 2 minutes ago. 4:02pm...

Do note that it never "finishes" per se, if it works the same as before when I tried it. You just quit it when you think it's done enough.

It differs from the windows defragmenter in that sense.

- arand

---

### Post by quirkification on 2010-06-15
Noticed that on MyDefrag, at 5:50 i just stopped it, and since then I've been running JKDefrag and seems to do a better job; But I do not see anyway to move the unmovable.

HEY HYE JUST FINISHED...but unmovable are still in the way of me shrinking a lot.

I can however shrink 12.4 GB instead of the 400MB from before.

only took 3 hours
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc3/hs067.snc3/13438_437376358967_658848967_5783706_7670640_n.jpg[/IMG]
Here is what the drive looked like when I was able to shrink down 12.4GB.
Then I realized that the top "yellow" files are the page files. So I deleted the use of page files and BAM

[IMG]http://hphotos-snc3.fbcdn.net/hs047.snc3/13438_437404593967_658848967_5784186_1351840_n.jpg[/IMG]
NOW I can shrink 60GB! Trying to improve some more.

Thanks so much for your help on defrag Arand

And thanks for the help with what I should do to boot a new Linux, Dino99

---

### Post by quirkification on 2010-06-16
So I was able to free 51GB from the grip of Windows 7 without doing a reinstall.
AS far as I know the windows 7 upgrade disk is NOT an install disk, right?
And being a linux Noob, I am unsure what a Swap drive is...but since I now feel safe with the space on the disk I have 10Gb of one, 4.5GB for school stuff and 51GB for overall spare.
\\:D/
[IMG]http://hphotos-snc3.fbcdn.net/hs067.snc3/13438_437451933967_658848967_5785277_259819_n.jpg[/IMG]

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc3/hs067.snc3/13438_437451873967_658848967_5785275_3493256_n.jpg[/IMG]

Again thanks for your help!!!):P

---

