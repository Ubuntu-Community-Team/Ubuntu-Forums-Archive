---
title: "New Install - Can't install Updates"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by Buschbarber on 2008-06-11
I just installed Ubuntu 8.04 Desktop on a 2Ghz Celeron machine This is my first introduction to Linux and Ubuntu.As I explore the Desktop, I see the Red Arrow that indicates 155 Updates. When I click on Onstall Updates, I see a rotating circle that is the equivalent of the Hourglass. I left the machine on, all night, and I was logged in. In the morning, nothibng had happened and the circle was still spinning. I rebooted and started the process again. Same result.

Everything else seems OK.

How do I troubleshoot this?

---

### Post by dstew on 2008-06-11
Open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
sudo apt-get update
sudo apt-get upgrade
```These commands do the same thing as using the Upgrade Manager, but we can see what the errors are, to tell why it is not working. Post to the forum the errors you get.

---

### Post by Buschbarber on 2008-06-11
I will try that, but I noticed one thing. If I bring up Update Manager,Uncheck all the Updates, and then only select a few Updates, I was prompted for my Admin password and then it proceeded to Download and Install the Updates. When it was finished, it presented me with the list of Updates, again. I unchecked all and then selected 7 or 8. It took longer, but eventually it Downloaded and Installed all that I had selected.

Is there a limit on how many Updates you can install, at any one time, without Hanging the system?

---

### Post by dstew on 2008-06-11
I am not aware of any limit, but 155 is rather a lot.

---

### Post by avtolle on 2008-06-11
Not directly responsive, but with 155 updates, the process of apt reviewing the database and determining what is to be installed, the current status of the various applications that are installed, etc., is going to take some time. As you have found out, reducing the number of updates to be installed to smaller "chunks" speeds up the process. Use of the terminal commands will be a bit quicker, and you will have the text coming by to keep you informed and entertained.

---

### Post by Buschbarber on 2008-06-11
Not being all that familiar with Ubuntu, I just took a guess as to how to diagnose the problem. 

The first couple of times I tried to run Update Manager, I did not get the request for my Admin Password nor did I see the Status Bar indicating the Updates were being Downloaded or Installed. Once I started checking 5 or so Updates at a time, the process started working. I did 5 Updates, then 10 Updates, then 20 Updates, then the remaining 120.

Is it possible that the server hosting the Updates could have been Slow or Down, late last night?

Next time I will try the Command Line approach. We former Windows types have to have a GUI or we are lost. That will change.

Thanks!!

---

### Post by dstew on 2008-06-12
The server being slow is often a problem. You just wait a day or two, and usually by then it's sorted.

---

### Post by Buschbarber on 2008-06-12
Thanks!! I thought that might be the case. I just had another 8 Updates today and all went well.

Ubuntu 8.04 2Ghz Celeron 768Mb Ram 250Gb HD SoundBlaster Audigy Nvidia 5200 256Mb Ram

---

### Post by Buschbarber on 2008-07-09
I was persuaded to install Unbuntu Ultimate. I did not know how to Upgrade to it so I reformatted the partition and then installed Unbuntu Ultimate.

Can you tell me what is different about Ultimate over the previous version?

As with the previous version, I had to reboot before the Update manager would Download and Install the updates. All went well this time.

---

