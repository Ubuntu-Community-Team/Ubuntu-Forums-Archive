---
title: "Rebooting stuck in grub menu intermittently"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by xandey on 2020-06-15
Hi, I am having this issue with 20.04 on a new Dell Inspiron 3593 where sometimes if I issue "sudo reboot" it will _occasionally_ get stuck in the grub menu. Initially it shows some errors:
- error: command failed (x several..) then…
- error: you need to load the kernel first…
Then it falls back to the grub menu. At which point the only recovery option is to manually reboot with the power button.

This was a clean install of 20.04 (minimal desktop), I have three of these laptops and have seen the issue with two of them (the other is still in the box). I tried reinstalling after turning everything I could think of off in the BIOS and have just seen the issue again.

I have run boot-repair: [http://paste.ubuntu.com/p/pnWxmwS5wq/](http://paste.ubuntu.com/p/pnWxmwS5wq/)
This is integrated graphics with: i3-1005G1 intel.
I have updated bios to latest: 1.8.0

My issues seems the same as this guy: [https://ubuntuforums.org/showthread.php?t=2441640&p=13958929#post13958929](https://ubuntuforums.org/showthread.php?t=2441640&p=13958929#post13958929)

Any help is greatly appreciated. Even suggestions of other support options.

---

### Post by oldfred on 2020-06-15
Not particularly a fan of one huge / (root) partition.
That is default installs and started with original Ubuntu years ago when drives were smaller & most dual booted.
If only Ubuntu, better to have separate /home and/or data partition(s). But then you do have more partitions to manage if starting to get full, so some trade off with more partitions, or too many partitions.

There used to be a bug with very old BIOS systems that could not boot from any file beyond 137GB on a drive. Those systems typically had 120GB or less drives and user installed new larger drive. But have not seen that type of error on any newer UEFI based system. 

You can try just shrinking / to 50GB or so and see if that helps, if you have not added a lot of data. If that works, then you can add /home and move existing /home to it or add data partition.
I normally suggest 30GB or / if using separate data or /home partition. But that depends on how much and how you want to organize your data.

---

### Post by xandey on 2020-06-16
I've done a bit more testing:
* I've been able to reproduce this more reliably. It seems that if I poweroff then poweron immediately (shutdown and hit power button as soon as power goes off) then it happens more reliably.
* I reverted to bios defaults "from bios" and then disabled secure boot as my bios settings to test.
* I have installed ubuntu 18.04 on two of these laptops which doesn't seem to have the problem so far, and I've been trying. grub 2.02-2ubuntu8.15
* I have shrunken the ext4 / partition down to 19.53GB and repeated the issue.
* I have entered the grub prompt and most commands give me "error: Command failed." message, but not all. 'true' fails, 'false' doesn't, 'ls' works, 'cat' doesn't...
* I grepped through the source code for grub 2.04 and found references in tpm.c (2.04-1ubuntu26 is the problem version installed), when i did the same for 2.02 there is no tpm.c.

So I'm thinking it's my tpm acting up on some power cycles. I think my best option is to file a bug report at ubuntu then deploy these laptops with 18.04 for now.

Sandy

---

### Post by oldfred on 2020-06-16
With that new of a Dell you probably should be using 20.04.

Always let system fully power down for 10-15 sec before rebooting. A cold boot then reloads all the configurations that UEFI fast start up fixes. If you have UEFI fast start up on in UEFI settings that could be part of issue. Fast start assumes no system changes, UEFI then does not scan system & operating system reloads previous configuration written from a previous boot. Changes then are not picked up and since no scan you may not have time to press any key to get into UEFI or UEFI boot menu.

You have to have kernel or system fully booted to use terminal commands. Grub's terminal just has a very few commands to help in booting manually.

Dell often needs additional drivers or settings with new systems. The have sputnik for that. The Dell with Linux currently shipping 18.04 include those extra changes.
And  they do give those changes to the kernel and driver developers, but it takes a release or two before everything is in a standard Linux distribution.
       New Dell 2020 & Sputnik history
[https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)
[https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en](https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en) 
    
With grub 2.04 we do have to add a boot parameter to get grub to work with loopmount. But have not seen that issue with anything else.
       2.04 Out of memory error loop mount
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)
[https://savannah.gnu.org/bugs/?57322](https://savannah.gnu.org/bugs/?57322)
[http://archive.ubuntu.com/ubuntu/dists/bionic/main/uefi/grub2-amd64/current/](http://archive.ubuntu.com/ubuntu/dists/bionic/main/uefi/grub2-amd64/current/)
A workaround is to run `rmmod tpm` before `loopback loop some.iso`. See
the linked Debian bug for more details.
Fedora isn't affected because it doesn't include tpm.

---

### Post by xandey on 2020-06-16
Well, I created my own bug report.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1883785](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1883785)

The bugs you mentioned looked similar but it seems like they are stuck on tpm issues all the time where as mine is intermittent. Their bug also is marked as fixed and merged and I think I should have it with my bug.

However, the 'rmmod tpm' seems to work for me as well. Is there any way to automate this ( or the sudo grub-install --no-uefi-secure-boot ?)

---

### Post by oldfred on 2020-06-16
I add things to grub in 40_custom which is added to boot stanza.
But grub processes scripts in number order & I would think that needs to be first.
I might copy 40_custom to 06_custom and add it there. And then after a sudo update-grub see if near beginning of /boot/grub/grub.cfg.

Just to have an original backup: 
       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup 
    
       sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom 
        sudo nano -B /etc/grub.d/06_custom
Then do:
sudo update-grub 

    
If you copy it correctly it should keep the execute bit. But if not.
       When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo chmod 755 /etc/grub.d/06_custom
or
sudo chmod a+x /etc/grub.d/06_custom

---

### Post by xandey on 2020-06-17
I think i'm ready to say this is fixed by your suggestion fred. Thanks a bunch.

for the record I do this:

sudo cp /etc/grub.d/40_custom /etc/grub.d/06_notpm
sudo bash -c 'echo "rmmod tpm" >> /etc/grub.d/06_notpm'
sudo update-grub

it also happens during installation sometimes but i don't mind retrying until the boot works.

---

