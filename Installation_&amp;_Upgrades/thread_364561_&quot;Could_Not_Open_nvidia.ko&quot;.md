---
title: "&quot;Could Not Open nvidia.ko&quot;"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by NotPhil on 2007-02-18
I waited to install the new kernel update because I was moving files from my old system to my new Linux box and didn't feel like re-installing the NVIDIA video driver at the time. But, silly me, I went ahead and did the updates last night, and now I'm having to boot from the old kernel (2.6.17-10) because the new one (2.6.17-11) tells me ...
```
FATAL: Could not open '/lib/modules/2.6.17-11-generic/volatile/nvidia.ko': No such file or directory
```
After the update, I re-installed the NVIDIA video drivers using the [instructions]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") at their site, which worked fine with the old kernel, but X-Windows wouldn't load. Then I downloaded [Envy,]("http://albertomilone.com/nvidia_scripts1.html") thinking I may have made some sort of typo, and a script might work better, but, well, it didn't get things working either.

Is there any way to get the new kernel to use NVIDIA's drivers? If not, how can I remove the kernel update? Will removing everything that says "linux" in synaptic work?

---

### Post by puccaso on 2007-02-18
i got the same problem with fglrx.ko and kernel 2.6.20-8-generic
i dont get it

---

### Post by SaveFerris on 2007-02-19
> **NotPhil said:**
> I waited to install the new kernel update because I was moving files from my old system to my new Linux box and didn't feel like re-installing the NVIDIA video driver at the time. But, silly me, I went ahead and did the updates last night, and now I'm having to boot from the old kernel (2.6.17-10) because the new one (2.6.17-11) tells me ...
```
FATAL: Could not open '/lib/modules/2.6.17-11-generic/volatile/nvidia.ko': No such file or directory
```
After the update, I re-installed the NVIDIA video drivers using the [instructions]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") at their site, which worked fine with the old kernel, but X-Windows wouldn't load. Then I downloaded [Envy,]("http://albertomilone.com/nvidia_scripts1.html") thinking I may have made some sort of typo, and a script might work better, but, well, it didn't get things working either.

Is there any way to get the new kernel to use NVIDIA's drivers? If not, how can I remove the kernel update? Will removing everything that says "linux" in synaptic work?

I had your same problem, I did so many things that I can't be entirelly sure what it was that did it, but I'm pretty sure that if you open up the security restricted repo and then sudo apt-get install --reinstall nvidia-glx nvidia-kernel-common it should help

I am fairly retarded, so...

Edit: Since that barely, if at all, helps anyone... I've saved the convo I had with a helpful guy on #ubuntu and uploaded it. (Note: I am jordan/SaveFerris/SaveFerr1s, the person helping me is jrib and the context into the beginning is i had just done $ nano /etc/apt/sources.list) If you need the log in another format, let me know.

---

### Post by NotPhil on 2007-02-20
> **SaveFerris said:**
> I had your same problem, I did so many things that I can't be entirelly sure what it was that did it,I finally got the drivers installed by running Envy again. I don't know why it didn't work correctly the first time, or why NVIDIA's installation method didn't work. Me thinks this kernel update is a little wonky.

---

### Post by SaveFerris on 2007-02-20
Ya, I do know that envy was the last thing I did before it started working again, so Envy is definitely the last step in fixing it.


I agree with your evaluation of the kernel.

---

### Post by DJMatus23 on 2007-07-20
Hi,

This has happened to me twice now, each time with a new kernel update.  Running Envy and getting it to install the nvIdIa drivers sorted it both times.  The annoying thing is, I'm running this on a freevo box, which my girlfriend almost trusts now...if this keeps happening, she might start complaining.  Is there a permenant fix for this?  Even just a way for me to call envy directly after a kernel update?

Alternatively, is there a way to just stop the kernel from updating automatically?

Thanks
DJM23

---

### Post by SaveFerris on 2007-07-21
As bad as it sounds, I would just not update the kernel if it's really a problem. Fiesty has a decent "restricted drivers manager" but getting into fiesty isn't always easy.

---

### Post by jaygo on 2007-10-15
I believe the instructions with Envy mention that you will have to uninstall the nvidia drivers (to get rid of the custom nvidia kernel) before upgrading your kernel, then reinstall with envy afterwards. 

That should take care of it. Kind of an advanced hack for now ... ATI open source drivers coming soon for the win.

---

### Post by falcon15500 on 2007-10-18
I had (have) the same problem.  After upgrading, my PC booted into a text mode login. Logs indicated that there was a problem finding the driver "nvidia.ko".  What I have found is that if I run **lrm-manager** from the command line, I can then "sudo /etc/init.d/kdm restart" and X will be fine.  It seems that my restricted modules aren't being loaded at boot properly.  Will look into it more later... I was doing this at 2am...

falc

---

### Post by falcon15500 on 2007-10-19
I was right.  The above solution can be adapted to work on every reboot.  All you have to do is edit <b>/etc/init.d/linux-restricted-modules</b>.  There is a line that says <code>lrm-manager --quick</code>
Remove the --quick, save the file and make sure that there is a softlink to that file in <b>/etc/rc2.d</b>

falc

---

### Post by quoick on 2007-10-19
I think the problem may be similar to what I was experiencing. They didn't enable the repositories by default with gutsy so you have to manually enable them. Go to **System - Software Sources**  and click on all the check boxes in the Downloadable from the Internet section. Allow it to refresh then the Nvidia restricted driver (along with any other software you will want to install will work.

---

### Post by falcon15500 on 2007-10-19
No, in this case the repo's are fine and the driver is there... It's just that the --quick restricted modules check doesn't appear to load them?  Removing the --quick flag seems to make it work fine...

falc

---

