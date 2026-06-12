---
title: "Hard drive was formatted durring the 12.04 update"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by DoctorLumpy on 2012-06-18
Hi!
I'm freaking out, I updated my mom's computer to Ubuntu 12.04 from 11.10 and when I came back to it after the install was done it wouldn't boot up. So I tried using a live CD, I tried installing it on a external hard drive, and I still can't mount the partition for the hard drive that I updated. I opened up gparted and it said that the whole hard drive was unallocated!!! I'm freaking out because it had all of my mom's family pictures on it, and she will KILL ME if I don't fix it (She doesn't know yet). She needs to bring it in to her work tomorrow so the tech guy can put Windows XP on it. PLEASE HELP

JAKE

Oh, the laptop is a Dell Latitude E6400

---

### Post by bcbc on 2012-06-18
Don't do anything to the hard drive that could overwrite the data. It's probably all there but may not be easily accessible depending on what has happened.

Boot from the live CD, select "Try ubuntu". Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

Also have a read through [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) - it can recover files (e.g. .jpg) from a formatted drive. You would plug in the external and recover to that.
To install photorec (while running a live CD):
```
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by DoctorLumpy on 2012-06-18
It says on the website that PhotoRec doesn't work on ext4 though :(

---

### Post by bcbc on 2012-06-18
Where does it say that?
It looks like it's just missing from the first reference to ext2/ext3. If you look further it mentions ext4 as well.

---

### Post by ddarsow on 2012-06-18
PhotoRec does work on ext4. The sooner after a problem the better though as files can be overwritten and rendered unrecoverable.

---

### Post by bcbc on 2012-06-18
Just a warning... photorec recovers a lot of stuff including files that were purposely deleted and also junk like browser cache. So you need to focus in on what you want to recover and then you have to go through a lot of stuff to find the ones (file types) you care about.

That said, it is very good at what it does.

---

### Post by DoctorLumpy on 2012-06-18
YOU GUYS ARE AWESOME!!!! THANK YOU SO MUCH!!!! Its recovering now, it should be done in a few hours (as long as it takes to recover 20 gigs of photos) BUT THANKS, Ya'll saved me so much trouble!!

---

### Post by Ambimom on 2012-06-19
Word of caution....put those photos in the cloud somewhere...dropbox maybe?  Ubuntu One?  Flickr? Photobucket?  ..... et.al. ad infinitum.  Lots of choices.

Then there's that old standby, CDs and DVDs.  

I only had to once lose irreplaceable photos as the result of a hard drive failure to learn my lesson.  I save the ones I want to keep in several different locations!

---

### Post by darkod on 2012-06-19
> **DoctorLumpy said:**
> YOU GUYS ARE AWESOME!!!! THANK YOU SO MUCH!!!! Its recovering now, it should be done in a few hours (as long as it takes to recover 20 gigs of photos) BUT THANKS, Ya'll saved me so much trouble!!

You sound happy and I do hope you get the data back, but you rushed into PhotoRec without need.

You didn't even take a look into the disk and the partition table. Often a simple small error or corruption in the partition table can make the disk display as without partitions because it can't understand the table with the error.
If you only write a correct table which takes 5 seconds, you can get all your original partitions back.

Then there is testdisk which is very good at recovering partitions and tables. And it keeps your whole structure, the OS, etc, and most importantly the filenames.

If I'm not mistaken, PhotoRec will recover loads of files with random names, etc. That's why it's the last thing to try, not the first.

But as long as you get your data back and you are happy with it, we don't mind what ever you use. :)

---

