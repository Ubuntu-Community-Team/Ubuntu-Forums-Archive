---
title: "New to Ubuntu, setting up partitions for dual boot"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Dakalador on 2010-06-02
So I wanted to dual boot Ubuntu with Windows 7, but have no idea how to partition out Ubuntu.  At the moment, I'm working with a 300GB harddrive that will solely hold installed applications and stuff like that.  Any shared/storage data will be put on separate harddrives altogether.

I plan on using a 40-50GB partition for Windows 7 alone (no installed applications and stuff).  And here come the questions about Ubuntu partitioning.  From what I read, do I only need three separate partitions? (/, /home, /swap)  Even then I'm not 100% sure what each of these partitions represent.  But my research says... / = equivalent to my Windows 7 partition, /home = the partition where installed applications go and other non-essential Ubuntu stuff, /swap = virtual memory

With all that said, to comfortably run Ubuntu can I have my partitions be these sizes?
/ = 10GB
/home = 20-30GB
/swap = 2GB (Do I even need this if I have 2GB of ram?)
Windows 7 = 40-50GB
W7 Apps = remaining space

I don't know what exactly I want to do with Ubuntu, but is a /home of 20-30GB adequate to install lot's and lot's of apps?

---

### Post by oldfred on 2010-06-03
Your partitioning is probably ok. I might make root larger. Actually all programs go into root. User setting and defaults for all your files go into /home. You can set up links so you data in other partitions appears in your /home as if it was there.

I generally recommend / (root) 10-20GB, swap 2GB or slightly larger than RAM if you want to hibernate. and the rest /home.

My root with many programs is 6GB. But for instance if you want to write a DVD it may make 4GB of temp files while writing so you may need some extra room in root.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

I mount a /share that is NTFS. And all the default data folders in /home using links from /data.
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

When I converted to Karmic I moved /home into its own 100GB partition, but then moved all my data into another 100GB partition (new hard drive). Now my /home is about 1GB as all data is in the /data partition. Only settings and some default data still is in /home.

---

### Post by sai koushik on 2010-06-03
i want to install ubuntu 10.04 on my studio in dual boot mode.

i tried to install , it installed , but after restrting from second time onwards blank screen is coming and boot options are not coming ,

i tried for 4 times but unsuccessful , i did below steps

-my hdd is 320 so i seperated 200(for win 7) , 50 (for personal ) , 40 unallocated for linux

-inserted ubuntu 10.04 rc1 cd

- in fourth step when selecting disk , i selected manual option(3rd)
- and i selected 40GB unallocated and formatted to ext4 and selected as root and install
- after reboot in boot options i can see 4 options i selected win 7 and from win7 i restarted
- after that black screen coming , boot options are not coming


can anybody help me please ?

---

### Post by Dakalador on 2010-06-03
Ah thanks, then in that case I'll probably have /home = 10GB and / = 25GB.

And I did forget to ask one question.  If I ever reinstall Windows  from a dual boot configuration, I would have to restore the GRUB boot loader afterwards? And I don't have to worry about anything if I reinstall Ubuntu?

---

### Post by darkod on 2010-06-03
> **Dakalador said:**
> Ah thanks, then in that case I'll probably have /home = 10GB and / = 25GB.

And I did forget to ask one question.  If I ever reinstall Windows  from a dual boot configuration, I would have to restore the GRUB boot loader afterwards? And I don't have to worry about anything if I reinstall Ubuntu?

Yes, if you reinstall windows it will overwrite grub2 on the MBR and you have to reinstall grub2 to the MBR again.
I didn't understand the question about reinstalling ubuntu, you only need to reinstall grub2 to the MBR in the above situation. Your ubuntu install will still exist on the hdd. Just windows bootloader can't boot or detect linux.

---

### Post by oldfred on 2010-06-03
Dakalador - Part of the reason my /home is as small as it is, is because I am real aggressive about making sure any program that normally writes data into /home or hidden files or folders in /home is converted to write into my data partition. I moved firefox & thunderbird profiles originally to share with XP and many other bits of data.

sai koushik - Please start a new thread with as much detail as you can give. This thread is on Dakaloador's partitioning questions.

---

