---
title: "Home Partition &amp; Fresh Install of Lucid"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by wblogan on 2010-05-05
I may have screwed up here and after hours of searching can't find an answer to my question.

I have a /home partition (/dev/sda3), 9.10 on /dev/sda7, and installed 10.04 on /dev/sda8.

--------------------
/dev/sda3: LABEL="home" UUID="12599671-6309-4372-8765-0a35cdb025fd" TYPE="ext4" 
/dev/sda5: UUID="56c53c24-62ef-457c-af6e-9cfc479e1cfe" TYPE="swap" 
/dev/sda6: UUID="918590cc-f12c-4065-bed0-de5385a42a9f" TYPE="swap" 
/dev/sda7: UUID="ce31e856-4b8c-4848-b7f5-b8f31dd89a8f" TYPE="ext4" 
/dev/sda8: UUID="b0f8aff0-263a-482d-a450-94b8a0e84936" TYPE="ext4" 
/dev/sda9: UUID="94da9dca-14ba-45f4-92c8-fd9f96e9113e" TYPE="swap" 
---------------------

9.10 mounts /dev/sda3 (home) on boot. Can I edit fstab and point /dev/sda8 (10.4) to /dev/sda3 (home)? If so, exactly what should I put in fstab? Or do I need to reinstall 10.4?

TIA.

---

### Post by mikewhatever on 2010-05-05
You should probably reinstall, even just to get rid of the two redundant swap partitions.

---

### Post by wblogan on 2010-05-05
> **mikewhatever said:**
> You should probably reinstall, even just to get rid of the two redundant swap partitions.

I was afraid of that. Hoping for a better solution I went ahead and began some of my post-fresh-install stuff. Oh well...

Do the redundant swap partitions hurt anything other than taking up disk space? (That there are two swap partitions is another part of my ignorance showing; not sure how I wound up with two, but now it's hard to correct for reasons I won't go into - it's the subject of another thread.)

Thanks for responding.

---

### Post by mikewhatever on 2010-05-05
Well, if you don't want to reinstall, don't. The redundant swap partitions just take up disk space, nothing more.

---

### Post by srs5694 on 2010-05-05
Reinstalling just to get rid of an extra swap partition is overkill. You can just disable it in /etc/fstab, and if you like, either change its type and mount it directly for some other use or expand some convenient partition to take over its space.

As to the original question, if I understand it correctly, you can certainly mount /dev/sda3 as /home on your new installation. The basic procedure is:


[list=1]
[*]Edit /etc/fstab in the new installation to add an entry for /dev/sda3 (or its UUID) to mount it at /home. Copying the entry from your old installation is a good way to do this.
[*]Type "sudo mv /home /home-orig" to move and back up the existing /home directory. You'll then be able to retrieve any files from there that you need, if you've created user files.
[*]Type "sudo mkdir /home" to create a fresh mount point.
[*]Either reboot or type "sudo mount -a" to remount the partitions, including /dev/sda3 as /home.
[/list]


An important caveat is that, if you used the same usernames on both installations, you'll end up with the same home directory for both. This will probably be fine for the newer installation; but if you reboot into the older one after using the newer one, it's conceivable that some programs will misbehave because they'll be confused by updates to their configuration files made by the more recent programs on your newer installations. There could also be missing icons or other quirks in either installation because of missing or changed icon files or other configuration file issues. Thus, it's best to use different usernames in the two installations, or to change the home directory used by the main user in one of the two installations. (If you've defined multiple users, you'll need to make similar changes for each. There may also be username/UID assignment issues in this case.)

---

### Post by wblogan on 2010-05-06
Thanks mikewhatever & srs 5694. I appreciate the info. Before you replied srs5694 I agreed with mikewhatever and took the easy route of reinstalling; no big deal. However, I did find that what you said is absolutely correct. When I logged back into the 9.10 installation I found some glitches; and when I logged back into 10.04 I found similar glitches. Nothing major (mostly theme related issues). So your information is valuable to me although keeping 9.10 was a backup measure in case 10.04 caused issues with my setup that I needed to work out. 10.04 is playing well with both my Dell desktop and laptop computers. So far so good! Thanks again for taking the time to respond. (If I knew how to mark this thread solved I would do it.)

---

### Post by mikewhatever on 2010-05-06
Wblogan, click 'Thread Tools' at the top of the page to mark the thread as solved.

---

