---
title: "GRUB stuck in Continual REBOOT - Help Please...Newbie.."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by RazorV on 2009-11-19
Okay I am totally NEW and totally LOST in the biggest way. I loaded Ubuntu on my 2nd internal hard dive in my HP Notebook. See my 'fdisk -l' below:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbb8555d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13297   106808121   42  SFS
/dev/sda2           13298       14594    10411647+  42  SFS


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3042211a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris

root@ubuntu:~# 


Everything was working fine after install of Ubuntu. I rebooted into Ubuntu many times &#8211; no problems. Then I reboot and went into Windows Visa (which is on my first harddirve) for the first time since I installed Ubuntu. Vista booted right up &#8211; no problem. 

I then shutdown Vista and my notebook rebooted. I get the POST then I see 'GRUB loading....' and then, my notebook reboots. It is stuck in a continual reboot.

Obviously Vista rewrote the MBR and now GRUB will not load properly.

Furthermore I have tried to reinstall GRUB but not sure what I'm doing.  When I run the command below It says STAGE1 not found.

grub> find /boot/grub/stage1

Error 15: File not found

grub> 



I also tried this:

# grub-install --root-directory=/boot /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot/boot: Not found or not a block device.
root@ubuntu:~# 


Please help me.  I really need to get my notebook running for work and I have tried and read everything and I am totally lost.

Thanks,
Greg

PS: I have tried the following and received the below:

# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:~#

---

### Post by daanvbaal on 2009-11-19
It's strange everything worked until you booted into vista. I have had about the same configuration as you for a while and never had any problems...

I'm not sure this is going to solve your problem permanently, but here's how to install grub:

You probably have some sort of live cd? I'm assuming Ubuntu. Start it and open a terminal (Utilities->Terminal).

Grub needs the /boot directory of your linux installation to configure properly, so we first have to mount it.

Create a directory for it:
```

sudo mkdir /mnt/ubuntu

```
Then mount the ubuntu system disk on it:
```

sudo mount /dev/sdb1 /mnt/ubuntu

```

Now it's time to use the grub-install command:
```

sudo grub-install --root-directory=/mnt/ubuntu /dev/sda

```

That should do it.

---

### Post by RazorV on 2009-11-20
Hey [daanvbaal]("http://ubuntuforums.org/member.php?u=789841")  thanks so much for the reply. Since my first post, I have reinstalled Ubuntu and now GRUB shows my Windows install and Ubuntu that I can boot into.  Right now I'm in Ubuntu and have rebooted many times into Ubuntu to get it set-up.  

I am so scared to boot into Windows Vista because of the Grub Error.  No one seems to be able to help me.  My question is to you, are you going to be around today or tomorrow to reply if your suggestion above does not work?  

I would hate to get stuck again and not have my main notebook working?

I do not have a STAGE1 file anywhere that I can find and that seems to be a major problem when trying to reinstall GRUB.  

Do I need a STAGE1 file in etc/grub?

Would you be avail via phone to help at all?  I know that's a lot to ask but I feel like I'm on a island alone and i really need my work notebook to function 100%.  It's been 2 days since I have been screwing around with this GRUB and trying to get it to boot again after going into Vista.

Also do you think my Trend Micro Corporate Internet Security Client is the cause of the MBR rewrite when I boot into Visa that would cause Grub to consistently reboot?

Thanks and I'll await your reply before I go into Vista and Grub gets screwed up again.  Sorry to ask so much of you.

Greg

---

### Post by daanvbaal on 2009-11-20
It indeed is a bit too much to ask me to be stand by in case something goes wrong. There is commercial support from canonical if you need something like that.

You always can get help here on the forum. With the grub-problem. The steps I describe above will succesfully reinstall grub to the MBR. You don't need to know where the stage1 file is. Just follow the steps.

If you need to be able to rely on your computer, you should choose for one OS. You could stick with ubuntu and simulate Windows in a virtual enviroment like Virtualbox. But the other way around is also possible.

I stopped using Windows years ago, so I can't help you there.

---

### Post by oldfred on 2009-11-20
It sounds like you are still using old grub but a similiar issue has been found on grub2 which writes a slightly large data area in the MBR. I would check if the trend micro is trying to protect the MBR also.

HP protect tools and Dell angel write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

