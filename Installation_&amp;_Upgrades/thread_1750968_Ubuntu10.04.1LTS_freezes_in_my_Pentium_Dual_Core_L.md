---
title: "Ubuntu10.04.1LTS freezes in my Pentium Dual Core Laptop"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by bkpsusmitaa on 2011-05-06
Dear friends,
I have installed Ubuntu10.04.1LTS in my Desktop amd64 computer. I also downloaded the same version for i386 processors and tried to install the OS for my HCL Pentium Dual Core T4300 @2.1Ghz 4GB RAM laptop, details of which are given in the following two screenshots:
[ATTACH]191301[/ATTACH] and [ATTACH]191302[/ATTACH]
I already have Debian Lenny 5.0.4 installed on the laptop [ATTACH]191300[/ATTACH] and the laptop works fine when I run the Debian OS or Knoppix liveCD image stored in the HDD of the laptop.
We all know that the Ubuntu LTS live CD leads to the following option:
[ATTACH]191303[/ATTACH] 
However, in my laptop the operation freezes before we can reach the above option. The screenshot explains the situation:
[ATTACH]191304[/ATTACH]
I know I could always use one of the alternate downloads and install the OS from it. But my point of contention is: where is the matter going wrong? Can't we use the graphical installer CD to do a CUI installation?
Could you advise on where I am going wrong?
Regards

---

### Post by mörgæs on 2011-05-07
What is CUI? 

I don't see any problem here. Just use the alternate version, as you mention.

Expecting the graphical installer to work on any given combination of hardware, knowing that some vendors are not very active in supporting Linux, is a bit much. 

The very reason for making an alternate ISO is solving problems like yours.

---

### Post by bkpsusmitaa on 2011-05-07
First of all, thanks, I understood as much, but that did not clear my query as to where the script went wrong. Is there a way of looking at the log file when the script goes wrong? Okay, maybe not all things are meant to be learnt, but I shall use the opportunity to thank you for your intention to help.
CUI is character user interface (or CLI - command line nterface, TUI - text user interface).
Regards

---

### Post by mikewhatever on 2011-05-07
You could try the following steps:
-hit any key as soon as you see the purple background
-you should see the old type live cd boot menu
-hit f6, then Esc, then delete the 'quiet splash' from the line at the bottom
-hit Enter to boot from the cd

The above should remove the splash screen and print lots of messages. Hopefully the last ones will give a clue as to why the process stops.

PS: GUI = Graphical User Interface.

---

### Post by bkpsusmitaa on 2011-05-08
Dear mikewhatever,
Thanks, now things are at least heading somewhere! I had used the alternate CD installer i386 by the time I read your message. By this time I also found that after the installation procedure the system comes to a stop while booting from HDD at Ubuntu progress bar.
I will now use your method to find out the problem.
Regards

---

### Post by tgalati4 on 2011-05-08
The i386 version will only see 3.2 GB of your RAM.  You need the i386-pae version or the amd64 version to see all of your RAM.  I don't know if the alternate installer has the pae version.

---

### Post by bkpsusmitaa on 2011-05-08
Dear mikewhatever,
I have followed those steps. A snapshot of the last set of output is in the attached file. Can you make anything from the screenshot?
[ATTACH]191528[/ATTACH]
Added later, after thorough testing:
You are correct. I followed the Debian system information application. It reports 2.5GB instead of 4GB of memory. Also, I used virtualisation and tested Ubuntu. It installs when memory is less than 2.5GB! And whether i386 or amd64, either of the CDs cause the same problem. And mikewhatever, I have tried your steps, but all of them lead to the same outcome.
So now, what to do? And what is this" i386-pae " version?
Regards,

---

### Post by mikewhatever on 2011-05-08
Not sure really. Can you take a closer shot of the last showing lines. Have you tried boot options like noapic, nolapic?

---

### Post by bkpsusmitaa on 2011-05-11
Dear Mikewhatever,
Please recall that I had enquired
> And what is this" i386-pae " version?
And you have said:
> Can you take a closer shot of the last showing lines
Like which ones?
Where do I find information about > noapic, nolapic...
Yes, I found it,... Documentation/kernel-parameters.txt...
Will get back to you shortly.
regards

---

