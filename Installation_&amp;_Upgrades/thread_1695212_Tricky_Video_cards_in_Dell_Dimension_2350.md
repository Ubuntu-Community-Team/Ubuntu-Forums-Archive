---
title: "Tricky Video cards in Dell Dimension 2350"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Hobbyist on 2011-02-25
So I've been using Linux on laptops and my desktop(with severe limits) for years and I finally decided to get serious with getting my desktop working right. My issue is this:

The desktop is a Dell Dimension 2350 with a Radeon 9200 video card. Linux runs fine with the on board card selected in the bios. The other option results in kernel panic. Always, forever and end of story. UNTIL: I figured the bios wasn't doing enough to hide the on board card and linux was just picking it up and trying to run with it anyway. So I blacklisted the kernel modules for my onboard card. This results in linux trying to use the other video card but results in x crashing. I do at least have consoles and that much is at least an improvement. What I am wondering is this: what do I do if the kernel modules for the radeon and the modules for the onboard card are the same? Is there a way to blacklist the onboard card instead of the module? Or do I just need the drivers for the radeon card and it will run without kernel modules?

---

### Post by Hobbyist on 2011-02-25
Bump for great justice.

---

### Post by Hobbyist on 2011-02-25
Bump. Again.

---

### Post by Hobbyist on 2011-02-26
One day I'm sure I'll get a reply but until then, bump.

---

### Post by davidmohammed on 2011-02-26
you didnt mention what version of ubuntu you are running...

have you tried 10.10?

Maybe you could try the newer ati graphics in the [x-swat ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by Hobbyist on 2011-02-27
I put all variants because the problem was with the linux kernel and not any specific distribution. I have however updated the kernel from command line and the radeon kernel module works. Thank you for the response.

---

### Post by AldenIsZen on 2011-03-04
> **Hobbyist said:**
> I put all variants because the problem was with the linux kernel and not any specific distribution. I have however updated the kernel from command line and the radeon kernel module works. Thank you for the response.
I am trying to help my father get Ubuntu on his 2350. I have been trying for years. Can I possible get you to reproduce and detail the steps you took? I am not sure what video card he has, but I can find out. Last time I tried, I don't think I could get Ubuntu to install even with the 3rd party video card removed.

---

### Post by Hobbyist on 2011-03-27
Hey sorry school kicked up and I haven't been on in ages, I hope you come back to check.
The 2350 has an issue in the bios that doesn't really hide the onboard card when you select (AUTO) in the peripherals section. Install Ubuntu with the onboard card selected. Then take the following steps.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```Scroll down to the end and add the following:

```
blacklist agpgart
blacklist intel_agp
```Next, restart the computer and go back to the BIOS. Select auto in the peripherals section for the video card(switch the monitor cable over so you don't get broken hearted over nothing lol). You should now be running on your PCI card.

I know my reply was late and I'm sorry. If you miss this post or get it first you'll be recieving a copy in your private messages as well. 

Happy Hacking!

---

### Post by AldenIsZen on 2011-03-27
Thanks for responding. It appears that I WILL have to have him take out the video card. I'm not where he is, and he is not very computer savvy, but we will get it done! Thanks again.

---

### Post by rudy1094 on 2011-04-09
Thanks for posting your solution. I'm new to Ubuntu and had this problem with my Dimension 2350. Your solution fixed it for me. Thanks.

---

