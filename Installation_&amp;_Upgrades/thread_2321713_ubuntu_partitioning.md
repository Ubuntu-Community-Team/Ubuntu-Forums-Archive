---
title: "ubuntu partitioning"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by florian.kapteina on 2016-04-24
Hi, following problem: I have a 24GB SSD Card (SanDisk SSD i100), such as a common 500GB HDD (Seagate ST9500325AS). So I'd like to put the main OS (Root-path) on the SSD (think this should be faster) and all other programs/files/applications I have or will install on to the common HDD. I'm not sure what to do exactly, I tried making a separated /home partition, but of course that only affects files and not installed programs/applications (think they're installed in /usr). So should I try to make a separate /usr partition ? Just wondering whether this is a useful solution or are there better ways to do this ?

---

### Post by Impavidus on 2016-04-24
You could make a separate /usr partition, but unless you're going to install an awful lot of programs, it should all fit on your 24GB SSD. That's easier and makes your programs load faster.

---

### Post by ajgreeny on 2016-04-24
As impavidus says, just manually partition at installation and put the root partition on the 24GB SSD and put everything else, /home or /data, and /swap on the HDD.

You will need to choose "Something Else" at the partitioning stage to do this but it should be well worth doing.

---

### Post by oldfred on 2016-04-24
My newest 16.04 install. I have not installed .wine & Picasa since Picasa is being obsoleted and trying to see is my wife can live with any of the other photo editors. She has used Picasa since XP days. So even less in /home than my other installs with Picasa as noted below.

 ```
fred@Asusz97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        24G  7.3G   16G  33% /
/dev/sda1       500M   21M  479M   5% /boot/efi
/dev/sdb4       385G  104G  261G  29% /mnt/data 
```

I do have /home inside / (root) but all data, including Firefox & Thunderbird profiles are in /mnt/data. My /home is tiny, du says and most is .cache:
180M    /home/fred

I configure system with shared data as I have multiple installs of Ubuntu and want all data available in each. Best not to share /home, so I share all data only.


 The actual user settings are small. My /home is 2GB (when I have .wine & Picasa) with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

