---
title: "Boot drive full - can't remove old versions"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by kdormuth on 2012-03-13
Hi all,
I'm running Ubuntu 11.10 (Oneiric Ocelot) and am getting a notification that my boot drive is almost full.  When I checked it, I saw that there are a bunch of older versions still there (for example, I have a file called abi-3.0.0-16-generic, but there's also abi-3.0.0-15-generic, abi-3.0.0-14-generic, etc).  I'm assuming these lower-numbered files are redundant copies, but I'm not sure how to get rid of them, or even what can be safely removed.  Any help would be appreciated!

Thanks,
Kristin

PS I apologize if this has been answered before; I tried searching but didn't find anything.

---

### Post by ajgreeny on 2012-03-13
It sounds like old kernels, though I have never seen them listed as abi-numbers.

Can you show the output of the command ```
cat /boot/grub/grub.cfg | grep menuentry
```which will show exactly what kernels are on your system.  Can you also show the output from ```
df -h
```which will show the OS partitions and amount of free space available on them all.

---

### Post by kdormuth on 2012-03-13
Here's the output:

cat /boot/grub/grub.cfg | grep menuentry
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Dell Utility Partition (on /dev/sda1)" --class windows --class os {

--------------------------------
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              56G  5.8G   47G  12% /
udev                  996M  4.0K  996M   1% /dev
tmpfs                 401M  1.2M  400M   1% /run
none                  5.0M     0  5.0M   0% /run/lock


Thanks!
-Kristin

---

### Post by coffeecat on 2012-03-13
@kdormuth, you have a total of 8 kernels installed for each of which you will have 5 files in /boot. The abi files are fairly small - the largest files are the initrd.img files followed by the actual kernel vmlinuz files. Don't delete them directly because there are many other files associated with each older and unwanted kernel in your /usr and /lib directories taking up space.

If you don't have Synaptic already installed, install it first and then use Synaptic to search for packages associated with each kernel in turn. Start with the search string "2.6.38-8" and work your way up to "3.0.0-14". Leave the 3.0.0-15 and 3.0.0-16 kernels installed. You will find 3 or 4 packages associated with each of those kernels. Mark all those packages for uninstallation and then click on Apply and let the package manager do the work for you. The advantage of this is that not only will it free up room in /boot, but it will also release space in /usr and /lib and will regenerate your grub menu so that only the 3.0.0-15 and 3.0.0-16 kernels show.

The reason I suggest leaving two kernels still installed is that it is a good idea to keep the immediately previous one to the latest in case of problems with the latest kernel. If you experience problems with the latest kernel you can boot into the previous one.

---

### Post by kdormuth on 2012-03-13
@CoffeeCat:

I have Synaptic; when I find the files, my options are "Mark for Removal" or "Mark for Complete Removal" (I don't see "Mark for Uninstallation").  Is this what you mean?

Thanks!
-Kristin

---

### Post by ajgreeny on 2012-03-13
@ coffeecat

Thanks for answering exactly as I would have done, but why was the OP getting a notification that the boot drive was almost full?

The **df -h** command only showed 12% used; nowhere near almost full.  Is there a maximum number of kernels allowed by the system that I am unaware of, or is the notification coming for other reasons?

@ OP

Yes that is what coffeecat meant, and you can "remove completely" without a problem.

---

### Post by coffeecat on 2012-03-13
> **ajgreeny said:**
> @ coffeecat

Thanks for answering exactly as I would have done, but why was the OP getting a notification that the boot drive was almost full?

The **df -h** command only showed 12% used; nowhere near almost full.  Is there a maximum number of kernels allowed by the system that I am unaware of, or is the notification coming for other reasons?

Thanks for spotting that - I missed the absent /boot. The 12% is the OP's root partition. I *think* the OP has accidentally omitted a couple of lines from their df -h output. There should be a "/run/shm" line after the "/run/lock" line so I guess the /boot line may have been omitted too.

@kdormuth, is that the whole of your df -h output? Is there any more?

Sorry for confusing you with "mark for uninstallation" - I was going from memory. ajgreeny is right - go for "mark for complete removal". That will remove the cached packages as well as uninstalling the kernels. "mark for removal" will uninstall the old kernels OK, but leave any cached packages which will simply take up HD space unnecessarily.

---

### Post by kdormuth on 2012-03-13
That did it!  Thank you both so much!
-Kristin

---

### Post by kdormuth on 2012-03-13
I tried to copy/paste the whole readout for the df -h command; it's possible I missed something.  When I run it now I get three additional lines from what I have in my previous post (but of course the % used is different since I removed the old files).  Sorry, I didn't see your reply till after I'd removed them.

-Kristin

---

