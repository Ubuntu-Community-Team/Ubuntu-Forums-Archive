---
title: "Problem with MergeList"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by bcrawford on 2011-05-17
Ok,
 I am new to the Ubuntu scene so bear with me(I do have some experience with Meego though). I have just done a fresh install of 11.04 on a dual-boot setup on my ASUS N53JF. It's been running rather smoothly although I have had a few issues.

When I attempt to run the update manager I get this message:

**Could not initialize the package information**
'E:Encountered a section with no package header, E:Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_maverick_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I then proceeded to try through terminal

sudo apt-get update

Get:35 [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                                                                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease
Get:36 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main amd64 Packages                                                       
99% [36 Packages bzip2 0 B] [Connecting to linux.dropbox.com]bzip2: (stdin) is not a bzip2 file.
Get:37 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                                                     
99% [36 Packages xz 0 B] [Connecting to linux.dropbox.com]/usr/bin/xz: (stdin): File format not recognized
Get:38 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_US
Get:39 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en
99% [38 Translation-en_US bzip2 0 B] [39 Translation-en 1,373 B]bzip2: (stdin) is not a bzip2 file.
99% [39 Translation-en bzip2 0 B] [Connecting to linux.dropbox.com]bzip2: (stdin) is not a bzip2 file.
99% [36 Packages lzma 0 B] [38 Translation-en_US xz 0 B] [Connecting to linux.dropbox.com]             1,324 B/s 3s/usr/bin/lzma: Decoder error
/usr/bin/xz: (stdin): File format not recognized
99% [39 Translation-en xz 0 B] [Connecting to linux.dropbox.com]/usr/bin/xz: (stdin): File format not recognized   
99% [38 Translation-en_US lzma 0 B] [Connecting to linux.dropbox.com]/usr/bin/lzma: Decoder error
99% [39 Translation-en lzma 0 B]/usr/bin/lzma: Decoder error         
Fetched 13.5 MB in 3min 18s (68.0 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_maverick_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



After a few minutes, I get the same error once it starts reading the package lists. I have tried running 

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

but with no success. 

On a seperate note, when I try to run the additional driver program from the control center, nothing happens. Any help would be greatly appreciated.

---

### Post by bcrawford on 2011-05-17
Don't know if it makes a difference, but the only thing I have installed was dropbox from their website using the official deb.

---

### Post by SwingKid on 2011-05-18
I have the same problem and I really hope that someone could assist us FAST with this please! I want to update my Ubuntu to 11.04 soon! Please help!

---

### Post by 2dfighter on 2011-05-21
I had the same problem, and this was the fix that worked for me.

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155500](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155500)

> Try:

sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
LANG=C;sudo apt-get clean; LANG=C;sudo apt-get autoclean
LANG=C;sudo apt-get update
sudo dpkg --clear-avail; sudo dpkg --configure -a
LANG=C;sudo apt-get install -f
LANG=C;sudo apt-get update
LANG=C;sudo apt-get dist-upgrade

---

### Post by ghibli on 2011-11-10
> **2dfighter said:**
> I had the same problem, and this was the fix that worked for me.

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155500](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/155500)
  THANK YOU VERY, VERY MUCH "2dfighter"!! I had the same problem with this MERGE etc. whatever -list and tried many advices from different forums with NO avail (though they were undeniably trying to help) . But YOUR advice worked fantastically for me too!! Machine works like a dream now with not too much time spend because of your "bingo"! Never one knows whose advice will work.

---

### Post by marisdembovskis on 2012-11-11
Thanks. 
Worked like charm!
dropbox manual install messed up, thanks for sharing this info!!!

---

### Post by wildmanne39 on 2012-11-11
Old thread closed.

---

