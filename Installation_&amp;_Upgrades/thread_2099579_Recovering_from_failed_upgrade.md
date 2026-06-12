---
title: "Recovering from failed upgrade"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by p2ranger on 2012-12-29
I was running a 10.04 LTS server. I tried moving up to 12.04 LTS server and I screwed something up during the upgrading process, hitting CNTRL C accidentally during one of the prompts. Of course this messed things up. Here is what I've done so far in my recovery attempts.

I pressed ESC during rebooting at the grub screen and was presented with a plethora of choices to try to boot from. I'm assuming it's different kernels? Not sure, anyway, I was able to get one of the recovery options to allow me to a prompt. The one with the highest number (3.2.0-35) allows me to boot up to a normal server prompt. 

Anyway, from there I did a 

dpkg --configure -a

and was able to finish stepping through all the configurations. The one I had messed up was for samba.

Once that was done I did apt-get update and apt-get upgrade and let it do its thing so that everything was complete.

Rebooting, it hangs. Here's some of the lines it gets through before it stops:

```

Boot from (hd0,4) ext2 244df...lots of numbers and letters..3bi
Starting up...
[ 1.628837] Kernel panic - not syncing: VFS Unable to mount root fs on unknown block(0,0)
[ 1.628891] Pid: 1, comm: swapper/0 not tainted 3.2.0-35-generic-pae #55-Ubuntu
[ 1.628930] Call trace:
[ 1.628972] [<c1592027>] ? printk+0x2d/0x2f
[ 1.629015] [<c1591ef5>] panic+0x5c/0x161
[ numbers ] [<more numbers>] mount_block_root+0xb9/0x14c
[ numbers ] [<more numbers>] ?sys_mknod+02x2c/0x30
[ numbers ] [<more numbers>] mount_root+0x59/0x5f
[ numbers ] [<more numbers>]prepare_namespace+0x14e/0x192
[ numbers ] [<more numbers>]? sys_access+0x25/0x30
[ numbers ] [<more numbers>] kernel_init+0x156/0x15b
[ numbers ] [<more numbers>]? start_kernel+0x353/0x353
[ numbers ] [<more numbers>] kernel_thread_helper+0x6/0x10

```

Then it hangs and the caps lock & scroll lock lights flash

I have tried using the boot/recovery Ubuntu CD. With this I'm able to get to a prompt again stepping through all the steps. The network says its configured, and I choose a partition to work with. I then get to a prompt.

When I get to a prompt, I can ping my router, but I can't get anything outside the network to show up.

As far as I can tell, when I tell it which kernel to load and it boots up, the server runs as it used to.

So, how do I get it so that I can reboot without having to stop it and select which kernel to load? 

Thanks for any help

Jason

---

### Post by p2ranger on 2012-12-31
Bump

---

### Post by Pjotr123 on 2012-12-31
Consider a clean reinstallation of 12.04.1 LTS? A clean upgrade would have been better anyway.... For all operating systems under the sun, on this our tired planet Earth. Upgrade woes are far too common.

---

### Post by p2ranger on 2012-12-31
That would be the ideal solution, but I have long since forgotten how to setup everything I did on my server. I made some notes which aren't complete, but I don't know if I will be able to get things running like I have them now. All my data (photos, music, documents, backups, etc) are in a separate safe place. I know the website I used to help me setup backuppc is no longer around, and that was a bugger to set up.

Jason

---

### Post by p2ranger on 2013-01-08
Did a complete reinstallation. Got everything working the way I want now. This time I took notes so I won't have to go searching the Internet on how to do everything if I have to do this again.

Jason

---

