---
title: "gutsy cant load nvidia modules"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by THEBIGEYE on 2007-10-28
hi, i have just network upgraded to gutsy, and the new kernel would not boot at all. so i am having to use the 6.20.14 kernel and now every time i try to install the restricted nvidia driver for my on board geforce 6100 and reboot it starts in safe graphics mode with plug and play monitor and vesa driver 
i have installed from the restricted manger and from binary this is most trouble ive had upgrading sines ive been using Ubuntu since 5.10. so i downloaded the iso from a mirror near me and when i try to do a clean install i get an I/O error on fd0?? ahhhh thinking about going back to feisty anyone else ahd any of these problems

---

### Post by frank.bommeli on 2007-11-03
I have exactly the same problem. I further tried Envy for installing nvidia's drivers. But get an error.

"linux-headers-2.6.20-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.20-16-generic has no installation candidate
Checking the Dependencies for the New Method"

I also tried the live cd which did not even start!
I have some other problems, but they may be related to either the kernel or the driver. I don't know.

Can anybody help with the driver problem?

Thanks in advance

---

### Post by Kuptis on 2007-11-04
I've been using (more like I've been trying to get things to work) Gutsy for about 4 weeks now.  Both my audio and video wouldn't work right.  

For audio I had no sound at all and when I tried to open the volume or do anything with sound I would get an error that there is no sound device.  After days of nothing working I upgraded to the 2.6.23.1 kernel and now at least I have sound.

For video, I have an onboard nVidia GeForce 7050 chip which also no matter what I have done so far does not work.  Even upgrading to the new kernel didn't help.  And now since I've upgraded to the new kernel I can't get things to work that rely on the kernel being what it was before (2.6.22).

I'm thinking of going with a mainstream distro such as pure Debian, Suse, Redhat, Mandrake/Mandriva.  From what I've seen across the web is that Ubuntu is so custom-patched that trying to use things outside of Ubuntu's packages may not work properly.

Not sure if what I said is what I'm trying to convey but getting things to work should not take me 3 weeks to do so (although I haven't gotten my video to work right yet and it's going on 4 weeks).  I can use it with the VESA driver but everytime I switch it to the nvidia driver it can't load right and switches itself right back to the VESA driver.

---

### Post by lightstream on 2007-11-04
I'm having these problems with my nvidia card too. I tried using Envy, also got the message about linux-headers package, which I couldn't find in the package manager for some reason. I found it [on this page]("http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-16-generic") (scroll down a bit to the "Download linux-headers-2.6.20-16-generic" heading and click on the i386 link - Firefox will open the package with the package manager which installs it for you)

I can now proceed past this step in Envy, but get this message now: "Bad luck, the kernel headers for the target kernel version could not be found"

Which doesn't make sense to me, as I thought that is exactly what the linux-headers-2.6.20-16-generic package contained?! The header files for the kernel source would be needed when compiling, so I assume Envy (or something it has initiated) is attempting but failing to compile a driver.

The other thing I've tried is to install [the Linux drivers from the Nvidia site]("http://www.nvidia.com/Download/index.aspx"). This is not going smoothly, seems to be some problem with the version of gcc it is trying to use to compile (?)

Anyway, gonna keep trying...

---

