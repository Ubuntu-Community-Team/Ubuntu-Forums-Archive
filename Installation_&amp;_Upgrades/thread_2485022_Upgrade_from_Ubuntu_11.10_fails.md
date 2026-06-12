---
title: "Upgrade from Ubuntu 11.10 fails"
date: 2023-03-17
forum: Installation &amp; Upgrades
---

### Post by pojak2011 on 2023-03-17
Hi,

I have a very old laptop with Ubuntu 11.10, that I'd like to upgrade to version 12 and then a modern version.
(The BIOS does not support UEFI.)

However, my attempts failed.
From other discussions, I've understood that [FONT=courier new]archive.ubuntu.com[/FONT] should not be called.
So I rewrote /etc/apt/sources.list as this:

$ cat sources.list
[FONT=courier new]deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse[/FONT]

And sources.list.distUpgrade as this:

$ cat sources.list.distUpgrade
[FONT=courier new]deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse[/FONT]

After having updated with [FONT=courier new]apt-get update[/FONT], [FONT=courier new]apt-get upgrade[/FONT] and [FONT=courier new]apt-get install update-manager-core[/FONT],
I tried [FONT=courier new]do-release-upgrade[/FONT].
But [FONT=courier new]do-release-upgrade[/FONT] failed with the message:

[FONT=courier new]Updating repository information
WARNING: Failed to read mirror file
No valid mirror found

[/FONT]An excerpt from main.log:[FONT=courier new]
2023-03-16 11:04:43,202 DEBUG rewriteSourcesList()
2023-03-16 11:04:43,208 DEBUG upgrade from old-releases.ubuntu.com detected
2023-03-16 11:04:43,209 DEBUG verifySourcesListEntry: deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
2023-03-16 11:04:43,209 DEBUG url_downloadable: [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)
2023-03-16 11:04:43,209 DEBUG s='http' n='us.archive.ubuntu.com' p='/ubuntu/dists/precise/Release' q='' f=''
2023-03-16 11:04:43,647 DEBUG error from httplib: 'HTTP Error 404: Not Found'
[/FONT]etc

It connects to [FONT=courier new]us.archive.ubuntu.com[/FONT] but that is not the right server, I assume.
I've searched in files but couldn't find the string us.archive anywhere. ](*,)

Do you know how I could make it connect to correct servers?

Complete output is in the do-release-upgrade.txt and, main.log and apt.log are also appended in 
this message (main.txt and apt.txt).

Best regards,

---

### Post by Impavidus on 2023-03-17
Are you sure you don't want a clean install? There are so many things that could (and probably will) go wrong on such a long string of release upgrades. Given the age of the laptop, probably best to use a lighter flavour. I currently run Xubuntu 22.04 on a laptop from 2011 and it works pretty well (Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz, 8GB RAM, 64 bit, legacy mode).

Does your laptop support 64 bit? If not, Ubuntu or any flavour is no longer an option. Can you give us some more specs of that laptop? We may be able to help you get the right OS installed to get some more years of useful life out of that laptop.

---

### Post by ne29914 on 2023-03-17
Don't even go there, you'll have a job for the next year or so.
Just backup your /home and do a clean ext4 install wiping everything.
Trust me, been there...

---

### Post by MAFoElffen on 2023-03-17
First get very good backups...

11.10 has been EOS since May 9, 2013. 12.00 LTS has been EOS since April 28th, 2017...

Though, I know you plan is to upgrade to current supported.

'Official recommends' would be to tell you that there is no clear upgrade path from 11.10 to current. Especially with trying to use 'do-release-upgrade'. That would be method 1 of 3 of how to upgrade a release. That will fail with such a gap in support.

Method 2 of 3, would be to tell you to get backups of your data that you want to keep, and do a Migration. Install current supported fresh... Install the programs you want. Then restore your backed up data. Clean fresh and the least problems without carrying over any fluff. This is actually the best and most recommended method, and should take under an hour to do.

Method 3 of 3, is what is called "The Debian Upgrade Method"... Make sure your system is upgraded to latest updates on the 'old-releases' repo. Then do this
```

# you will only have to do this step once...
sed -i 's/normal/lts/g' /etc/update-manager/release-upgrades
# this is the step to go from one short step, to get from one release to another...
sed -i 's/oneiric/precise/g' /etc/apt/sources.list

```
Which will change the release from 11/10 to 12.04... Then 
```

sudo update && sudo dist-upgrade

```
Wait until done... Hopefully without errors. (no guaranty)

Then 'rinse wash, rinse, repeat' of changing the release codename from LTS to LTS in one step increments.

My disclaimer: Note that this is risky and not officially recommended. Do not, for any reason try to go more than one LTS step at a time, or it will result in instant failure.

When you get to Xenial and are pointing to the Bionic repo's, then also do this:
```

sed -i 's/old-release/archive/g' /etc/apt/sources.list

```
Going step by step, from one release to another, takes a very long time, and has many, many, many repeated chances for errors to occur.

You have been duely warned that this is risky. Make sure you do a good backup of your data first, so if necessary, that you can fall-back to the interim to the '2 of 3' method of Migration.

---

### Post by pojak2011 on 2023-03-18
Thanks a lot to all of you who responded! 

I went for Ubuntu version 22.04, a minimal installation, erased disks, and it got OK. :)

The laptop is an Asus Notebook with an AMD E-450 APU processor, 1.65 GHz, 64 bits,
and with 4 GB RAM.

(Before I tried with Ubuntu 11.10, I tried with Xubuntu 22.04, but that installation
went wrong. It couldn't install GRUB.)

Best regards,

---

### Post by ne29914 on 2023-03-18
Glad it worked. 
That hardware configuration is somewhat marginal for Ubuntu, I'd go for a lightweight distro instead, like Lubuntu or Xubuntu.

---

