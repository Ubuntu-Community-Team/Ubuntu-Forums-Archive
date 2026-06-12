---
title: "Documents on 2nd drive"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by Manfredcherry on 2012-08-15
Hello
 
I have an EEE PC 900 (4GB + 16GB) with EasyPeasy and would like to link all the " Documents, Pictures, Music...." with subfolders to be safed on the 16GB drive? Can that be done?
 
Thanks           Manfred

---

### Post by Bucky Ball on 2012-08-15
Yes. I do the same with /home. 

Here's an example of if you wanted to move things in your /home directory to another partition and then link them in your original /home. Basically you need to:

* Copy the contents of your /home directory (except 'Desktop') to a directory somewhere on the partition you're wanting to use;
* Delete the originals (after checking your data is safe on the other partition);
* Create symlinks in the /home directory linking to directories on the other partition;
* The syntax to do that is like this, for example:

```
ln -s /media/16Gb_directory/Documents /home/your_user/Documents
```You obviously need to change the details to match what you have but it is:

```
ln -s /the_existing_folder /the_link_to_it
```Hope that's understandable. If not, just ask. ;)

---

### Post by Manfredcherry on 2012-08-20
Hello again
 
I have tried a few variations of typing this line in but has not worked, couldn't get past the line "unknown command".
 
But I would like to learn this to work in the Terminal window, I'm sure somebody can send me some links to online Linux Books? But like very basic start.
 
Back to the initial question, I was still looking for a good version to fit on my little 4GB SSD drive and experimented with partitioning and have now installed Mint 13.!!
 
What I did was to partition the whole 4 GB complete as the main (primary - ext4 - mounted in /) and on the 16 GB I put 1.6 GB (logical) - swap area and the rest as primary - ext2 - mounted in /home. This way I can fit Mint 13 on the 4GB and have all the docs on the 2nd drive automaticaly. The EEEPC sees those 2 drives as 1 now - that's how I understand it anyway.
 
Thanks           Manfred

---

