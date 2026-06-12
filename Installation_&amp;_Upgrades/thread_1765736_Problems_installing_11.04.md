---
title: "Problems installing 11.04"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by markyork on 2011-05-23
Due to graphic issues with the gui installer I attempted to install Ubuntu 11.04 using the alternate installer. I got through the installation (somewhat), but still ran into issues doing it that way. I'd appreciate anyone's help!

First, I'm installing on a brand new Toshiba laptop. It has a 500GB drive and I have a 200+GB undefined (unallocated?) section of the drive that I'm installing Ubuntu on.

I went through the text-based alternate install (God help the **non**-computer geek who tries to install using that method!). A couple of things I have to deal with as a result of installing: 

1) During the install I was dismayed to find that the installer couldn't recognize my network card. I didn't know what to enter for either the DHCP info, nor the IP address info (I'm on your standard home DSL wireless router setup with a network key and using DHCP), so I just chose to skip that until the installation is done and I can install the driver manually.

2) Whether I just missed it, or the options aren't there for the alternate install, I never saw the chance to set the "home" and "/" partition sizes, although there was a step involving the swap size, but I just left it at the default of something like 4.6 or so.

3) Finally, the reason for using the alternate install in the first place - graphic issues - reared its ugly head again. On the first reboot after the installation process, I got the same graphic anomalies as when I tried the Wubi and standalone gui installations.

When I was at the boot choice menu (the one which allows you to choose between the kernels (I think), Windows, and recovery options for each - the GRUB menu, I believe), I highlighted the top-most one and pressed "e" with the intention of using "nomodeset", as recommended to others experiencing graphics issues. But the resulting screen after pressing "e" and then Enter threw me off. It had a bunch of lines which I assumed to be commands that were to be carried out during boot. I could write over any of them and there was one blank line, so I entered in nomodeset in that line, but I got a message saying nomodeset was an unrecognized command.

So I need to deal with a few things here:
1) figuring out how to get a network driver installed

2) I need to resolve the partitioning issue: everything I've read says that if I ever want to upgrade Ubuntu I will want the home directory in its own partition. Can I do that post-installation? At this point I'm not averse to scrapping the installation and reinstalling if necessary

3) I need to get the graphic issue resolved

Please, when offering advice on commands to enter, keep in mind that I was lost when I used the option to edit the boot command! Simply saying "edit the normal ubuntu boot line to include nomodeset" (a quote from someone to me offering help about the graphics issue in another post) won't do it. As I said above, I tried that and wasn't even sure if I did it right or if I entered it on the right screen! "You'll see this on the screen. Enter this text here, and when you do you'll then see this on the screen" is what I need at this point to know I'm doing stuff right.

I'd also be happy to provide system information output if necessary, just please tell me how to get to a command line from the GRUB menu, what commands to enter, and then how to get that output in a form that I can use to post here! ;)

Thanks a lot for anyone's help!

---

### Post by HalfEmptyHero on 2011-05-23
There are a few things you need to do. The partitioning thing is part  simple, but depends on how you are installing. The gui installer will  work, you just have to add nomodeset. When the boot menu for the livecd  comes up you should see an option for Other Options (or something like  that) I believe it is F6. You hit that, and you will see a list of  options, one of them being nomodeset. I have never been able to get it  to work by choosing an item from the list, it's a bug I guess, so hit  escape and you will be able to type in nomodeset. You'll see what I  mean. When you get to partitioning, choose manual. You will then be able  to set up your partitions as you desire. I recommend 10GB for root, and  whatever you want for home. Don't forget your swap either.

The alternate installer also has the manual partition option, choose that if you are using it.

If I had a picture of the boot options, I could show you where to put  nomodeset, but ubuntu isn't currently installed on this computer. (Edit: it goes after quiet splash) Your  other option is to boot into safe mode with networking from the recovery  mode option in grub. You will need an Ethernet connection as wireless  won't work. Install the graphic drivers with the following commands:
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Keep in mind there will be a few issues with  your laptop on Ubuntu. For one, your memory card reader will not work.  There was a way around this on 10.10, but it doesn't work on 11.04. Your  mic also won't work. Others with similar laptops have gotten it to  work, but I have had limited success. Your hdmi audio probably won't  work by default, I can't remember if it does in 11.04 or not. If it  doesn't I can show you how to fix that.

---

### Post by markyork on 2011-05-23
> **HalfEmptyHero said:**
> There are a few things you need to do. The partitioning thing is part  simple, but depends on how you are installing. The gui installer will  work, you just have to add nomodeset. When the boot menu for the livecd  comes up you should see an option for Other Options (or something like  that) I believe it is F6. You hit that, and you will see a list of  options, one of them being nomodeset. I have never been able to get it  to work by choosing an item from the list, it's a bug I guess, so hit  escape and you will be able to type in nomodeset. You'll see what I  mean. When you get to partitioning, choose manual. You will then be able  to set up your partitions as you desire. I recommend 10GB for root, and  whatever you want for home. Don't forget your swap either.

The alternate installer also has the manual partition option, choose that if you are using it.

If I had a picture of the boot options, I could show you where to put  nomodeset, but ubuntu isn't currently installed on this computer. (Edit: it goes after quiet splash) Your  other option is to boot into safe mode with networking from the recovery  mode option in grub. You will need an Ethernet connection as wireless  won't work. Install the graphic drivers with the following commands:
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Keep in mind there will be a few issues with  your laptop on Ubuntu. For one, your memory card reader will not work.  There was a way around this on 10.10, but it doesn't work on 11.04. Your  mic also won't work. Others with similar laptops have gotten it to  work, but I have had limited success. Your hdmi audio probably won't  work by default, I can't remember if it does in 11.04 or not. If it  doesn't I can show you how to fix that.

Thanks for re-replying in this thread, HalfEmptyHero!

I'll post my results here.

---

### Post by HalfEmptyHero on 2011-05-23
When you are doing the manual partitioning, you will see an option that says mount point. This is where you put in / for the root partition and /home for the home partition.

---

### Post by markyork on 2011-05-23
Thanks.

I'm copying/pasting all your info to a doc to have handy while I try this out...

---

### Post by markyork on 2011-05-23
> **HalfEmptyHero said:**
> (Edit: it goes after quiet splash)

In the context of your instructions, exactly what do you mean by this?

---

### Post by markyork on 2011-05-23
> **HalfEmptyHero said:**
> Your  other option is to boot into safe mode with networking from the recovery  mode option in grub. You will need an Ethernet connection as wireless  won't work. Install the graphic drivers with the following commands:
```
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Keep in mind there will be a few issues with  your laptop on Ubuntu. For one, your memory card reader will not work.  There was a way around this on 10.10, but it doesn't work on 11.04. Your  mic also won't work. Others with similar laptops have gotten it to  work, but I have had limited success. Your hdmi audio probably won't  work by default, I can't remember if it does in 11.04 or not. If it  doesn't I can show you how to fix that.

The problem with this solution is that the installation wasn't able to recognize my laptop's network card, so wireless or wired, I've got no Internet until I can figure out what driver I need, put it it some where Ubunutu can find it, and then enter in the commands to install it.

---

### Post by HalfEmptyHero on 2011-05-23
That's weird. I have an x505 Q880, and have no problems with ethernet. The wireless works fine too, I simply don't know how to set that up from the command line. The q880 and q882 I believe have the same network card, not sure what's up there. If you can boot into low graphics mode, see if you can connect to wireless. This pic was what I meant by quiet splash. You add nomodeset after it. Yours might not look exactly like this, but that's where you put it.

---

### Post by markyork on 2011-05-23
Wow! It's great that I found someone with a running copy on a laptop very similar to mine! (The thing is flippin' big, isn't it?!)

That is truly odd about the network card, since yours works - no reason to think they'd be very different - if at all...

Thanks for the pic - that's exactly the screen I saw. When I got there I added nomodeset in the blank line near the top.

Your pic makes it crystal clear where I need to do that!

Thanks again - I'll let you know how turn out.

---

### Post by markyork on 2011-05-23
Just thought I'd pop in here and give an update.

HalfEmptyHero, your screenshot was very helpful. I noted where you entered nomodeset and it worked!

I did notice a few warnings as it was booting, which I can't remember now, but the main battle is over: just getting in!

Oh! And when I got to the desktop I was informed that wireless networks were available, so that issue is done as well.

Just gotta get the graphics issue resolved and I'm up and running...

---

### Post by markyork on 2011-05-23
Well, I expect I should be fine from here on out.

I'm writing this from the Firefox browser in Ubuntu and in the process of downloading my graphics driver using the lines HalfEmptyHero entered above!

To deal with the partitioning issue mentioned above, I just re-ran the installation and selected nomodeset in the F6 menu.

Thanks a million, HalfEmptyHero - you're my FULL hero! :)

---

### Post by HalfEmptyHero on 2011-05-24
Glad I could help ;)

---

