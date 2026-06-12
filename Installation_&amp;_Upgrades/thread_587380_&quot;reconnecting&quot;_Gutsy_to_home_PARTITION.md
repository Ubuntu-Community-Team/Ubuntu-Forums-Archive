---
title: "&quot;reconnecting&quot; Gutsy to /home PARTITION"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by t2000kw on 2007-10-22
I've had some problems upgrading to Gutsy. When I tried to upgrade it trashed my / folder. When I reinstalled Feisty, allowed it to run the 125 security updates on it, that also trashed the / folder and rendered it unbootable.

This time I'm installing Feisty, NOT allow the security updates to take place, download Gutsy, burn a CD if I can (had problems recently so it may be a bad CD-R/DVD+/-R drive but I have a backup drive), then upgrade to Gutsy. 

Once I upgrade, how do I get it to point to my /home PARTITION (it's separate from the Feisty or Gutsy new installation and has all of my saved documents, etc., in it)?

I can find information on MOVING /home to a /home partition but not fixing a new installation  so that it uses my existing /home PARTITION. This is not just a folder in the / partition. It is a separate partiton. I just want to make that clear so that I don't get advice on how to move it to a partition by copying the files over. 

It's probably a matter of doing some of the stuff mentioned in some forum posts, but I don't want to make the mistake of deleting or doing something I shouldn't.

Thanks in advance. 

I will post this in another one of the sub-forums but this seemed like an appropriate one since a person upgrading might need to address this item.

---

### Post by louieb on 2007-10-22
When you install  use the manual partitioning option.  There you select the partition(s) to use for / and /home. and if you want to format them. Just don't format /home and you should be all set.

---

### Post by t2000kw on 2007-10-22
I tried that and the /home partition got trashed somehow. I did make sure it said to NOT format (it was unchecked) that partition. I might have missed it offering to resize the partiton since when I tried another reinstall of Feisty after the security updates messed it up, I noticed it wanted to resize everything I set for a partition to be used. 

Is there an unerase utility I can use?

It's not a major disaster, but it would be nice to get a couple of my documents back.

Don

---

### Post by louieb on 2007-10-22
Might try with the live CD to browse your hard drive and see if you can find your documents and copy the off to a usb stick.  I haven't used the Ubuntu live CD to copy data off so not sure  how to do it.

What I use is [Knoppix Linux]("http://www.knoppix.net/") or  [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") both are great Live CDs. Knoppix is easier but you need 512mb ram,  Puppy runs in 128mb and it not hard to use. 

If you didn't format your /home my guess is the data is still there. 
With your PC kinda trashed at this moment might be a good time to plan a partition scheme and after you get your data off start with a fresh  install.

Don't know how you plan to use our PC  but if you look at the Dual Boot and psychocats  links in my signature. Both sites have some partition layout suggestions.

---

