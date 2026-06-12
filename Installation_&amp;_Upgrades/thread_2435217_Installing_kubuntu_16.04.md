---
title: "Installing kubuntu 16.04"
date: 2020-01-17
forum: Installation &amp; Upgrades
---

### Post by darthgollo on 2020-01-17
Hello, how are you doing guys, I do really need some help in here. I  have been trying to install any type of linux dristo in my computer and  has been so difficult to do it with any lastest version i have tried.  tho, I finally installed kubuntu 16.04 but at the end the wifi signal is  not working and I would like to fix this. I will appreciate any advice  to fix it. my computer is HP Pavilion x360 15-bk010nr (W2M08UA) Laptop  (Core i5 6th Gen/8 GB/1 TB/Windows 10)  Intel Core i5-6200U AND 8GB ram.  and it is so difficult to install any distro, why? when I am trying to  boot any iso image most of the time it can not boot because it is  loading. but I want to fix kubuntu. Thank you

---

### Post by jeremy31 on 2020-01-17
Moved to Installations and upgrades

---

### Post by CelticWarrior on 2020-01-17
If Kubuntu is actually installed then please post the result of ```
[FONT=SimSun]`lspci -knn | grep Net -A3`[/FONT]

``` terminal command so we can identify your WiFi card.

---

### Post by TheFu on 2020-01-17
> **darthgollo said:**
> ... and it is so difficult to install any distro, why? when I am trying to  boot any iso image most of the time it can not boot because it is  loading. but I want to fix kubuntu. Thank you

Have you tried to install Windows with an existing Linux already?  It isn't possible.  The Windows installer always wants to wipe the disk or so I'm told.

We can thank Microsoft for the added complexities. For example, Microsoft calls things "drives" that aren't actually a disk drive.  C: isn't a drive. D: isn't a drive.  They are partitions, but to dumb things down instead of using the correct terms, people routinely come from a Windows background using incorrect terms.   Very often, the issue is with a lack of knowledge and understanding the correct use of computer terms that causes issues.

Little things are needed pre-install - like making room for Linux to install onto the storage.  People coming from Windows make all sorts of assumptions because they don't know any better. Their knowledge of different OSes is very limited.  For example, they think NTFS is used by every OS.  It is not.  Linux cannot be installed onto an existing NTFS partition that is used by Windows.  So, if you want any hope of installing a Linux onto the disk, you'll almost certainly need to defrag all the partitions, then shrink one or more partitions and perhaps delete 1 or more partitions, to make room for Linux.  If that sounds hard, well, it is.  

But if you want to wipe Windows, then installing most Linux distros shouldn't be too hard, unless there are hardware incompatibilities or hardware faults.

At our local installfests, we routinely have seen issues with HP computers needing special help for installation.  All I can suggest is to take the exact model, then add "ubuntu 18.04 install" to that and google for results.  Chances are that someone else has tried and documented any needed fixes for troublesome hardware.  While it is fresh in your mind, take notes so in 3-12 months you'll have those notes for the next install. Keep the notes safe.

I understand that my effort to explain things above may be completely lost.  Installing an OS is like putting a new engine into a vehicle. It is not a trivial thing for a beginner.  If you want to install multiple engines, things get more complicated.

There is an alternative which may or may not be easier.  Use virtual machines.  You can't go completely crazy, but you can definitely run a Kubuntu VM on the hardware you have, assuming there is sufficient free storage available.  You won't even need to create a new partition.  For non-GUI stuff, a properly tuned VM can provide 90-95% of native performance.  With a heavy GUI like Qt provides, the GUI performance won't come close to native, but it might be sufficient for what you need. Hard to say.  For typical office productivity applications, using a VM is more than acceptable, IMHO.  I've been running Linux desktops inside VMs almost 15 yrs now.

---

### Post by mörgæs on 2020-01-18
Kubuntu 16.04 is out of support so it's not an ideal solution.

Pen-and-touch computers are often a problem because it takes time for the GNU/Linux community to provide drivers. Are you able to do a live boot of 19.10 using wired internet connection? 

Here is some more [advice]("https://ubuntuforums.org/showthread.php?t=2431160") which could come in handy.

---

