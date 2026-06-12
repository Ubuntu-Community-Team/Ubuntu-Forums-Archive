---
title: "Installing a kernel from live kubuntu cd"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by rl2401 on 2013-09-19
I am a new user and dont know much about OS and kernel for that matter.

I was installing/updating/uninstalling software using synaptics package manager and I may have uninstalled linux-image-xxx (xxx stands for some version number).

The whole process went smoothly but after reboot the pc is not starting. The bios loads but after that it shows a blue screen and restart to repeat the same thing again and again. On further search I found out that these are kernel related files.

I have important data on my machine so I do not want to reinstall Kubuntu.

Is there a way I can install the kernel on my internal hard disk from kubuntu live cd.

I have search and so far I feel that a combination of these two links could help me:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UjrA3n_4Xms](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UjrA3n_4Xms)
[http://askubuntu.com/questions/142192/can-i-install-linux-kernel-3-4-in-ubuntu-and-kubuntu-12-04](http://askubuntu.com/questions/142192/can-i-install-linux-kernel-3-4-in-ubuntu-and-kubuntu-12-04)

I am using kubuntu 10.04

Any help/advise/hints/links would be greatly appreciated. Even if it is a matter of can be done or not I'd like to know it.

Thanks

---

### Post by TheFu on 2013-09-19
I don't know the specific steps, sorry.

That is a tough problem if really true. I didn't believe that any package manager would uninstall (remove/purge) the actively running kernel. Perhaps I'm wrong.  Put the liveCD into the drive (CD or flash), select try ubuntu and it should see all your files and settings under /home and /etc.  Back those up to other media.  Learn more about backups and use them, religiously.  Then reinstall the system to your liking, restore the data and settings, be happy.

It might be possible to use boot-rescue (see my signature) and revive your machine, but that isn't really what the tool is designed for. A prior kernel should still be installed, so there is hope.

You can save the list of packages currently installed and use that list in the new installation, if you like.  **dpkg --get-selections** is the command - you'll want to read up on the specific use, then use --set-selections at restore time.

I wrote an article for Lifehacker about [System Maintenance for Ubuntu/Debian PCs]("http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs"). That is the source article with some recent updates.

Also, 10.04 has been non-supported since May. 12.04 is an LTS release and will be patched until 2017 - highly recommended. Your 10.04 system is NOT secure anymore and hasn't been for months. It is dangerous to use it on any network.

---

### Post by rl2401 on 2013-09-20
Thanks a lot for your help. I found the right approach explained in detail [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) the answer by @Eliah Kagan, was totally apt for a newbie like me :)

---

### Post by VMC on 2013-09-20
> **rl2401 said:**
> Thanks a lot for your help. I found the right approach explained in detail [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) the answer by @Eliah Kagan, was totally apt for a newbie like me :)

That (Eliah) has to be the most complete detail fix I have ever seen. Also, if satisfied, mark this topic as solved.

---

