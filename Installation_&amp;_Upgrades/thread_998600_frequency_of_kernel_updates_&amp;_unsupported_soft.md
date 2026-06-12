---
title: "frequency of kernel updates &amp; unsupported software"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by razzz on 2008-12-01
Greetings all,

Can anyone comment on how often kernel updates are made to LTS versions of Ubuntu that can potentially stop unsupported software from working? Please excuse me if this sounds like an odd question. I am more of an end user than a programmer.

I have a small business and have been running Ubuntu on my servers since spring of 2007. Since then, I have been working on learning Ubuntu and finding solutions to convert my dozen plus workstations from XP to Ubuntu. Last week, I finally felt confident enough to begin the migration. 

Everything was running really great for a week until I downloaded and installed the latest security updates which included a kernel update. This broke VMware. Our order entry system will only run in windows and we were dead in the water. I was able to get things back up and running however it did give me a brief panic attack.

I am running XP in VMware as I could not get the Ubuntu supported VirtualBox to recognize the CD drives in order to install the guest OS.

Besides VMware, I just ordered, over the phone with Intuit, a Linux version of QuickBooks Enterprise Pro 2009. The guy on the phone said it would run on Ubuntu however I just checked Intuit's site and it doesn't make mention of Ubuntu or Debian. In any case, if it will run on Ubuntu, I am guessing it also may never be in the supported repository as it is not open source. And thinking ahead, when other popular software makers begin to provide their software for Linux, will their packages some day be supported by Ubuntu? 

I do realize that a good OS is a work in progress and that there will always be changes and updates. In my particular situation, where I am using unsupported software... 

Should I turn off all updates and wait until the next LTS release?
How dangerous is turning off the security updates?
(our servers are not providing any internet services)
Are there certain types of updates I should avoid?


Any suggestions or in site would be greatly appreciated.

---

### Post by cariboo on 2008-12-01
Unless there is a compelling reason to update the kerenl, I wouldn't bother until it is more convenient to reboot the server and you have the time to repair a problem if something fails. For mission critical servers, you shouldn't update the kernel unless there has been a security flaw that affects your setup.

Edit: I would suggest checking here:

[http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

For any security updates.

Jim

---

### Post by razzz on 2008-12-01
Hey Jim,

Thanks for the useful link. In my situation, all the workstations and the servers are mission critical when we are open. I am going to save doing updates for Fridays end of business day. So if anything would ever happen I have all weekend. 

Thanks for the reply.

Steve

---

### Post by dwasifar on 2008-12-22
> **razzz said:**
> Besides VMware, I just ordered, over the phone with Intuit, a Linux version of QuickBooks Enterprise Pro 2009. The guy on the phone said it would run on Ubuntu however I just checked Intuit's site and it doesn't make mention of Ubuntu or Debian.
If I understand correctly what I see on the Intuit site, the back-end database and file servers can run on Linux (they specify SUSE or Fedora), but the QuickBooks desktop application itself must run on XP or Vista. 

I've been running QuickBooks 2000 using Crossover Office for some time now.  Staples has a deal for today only ( 12/22/08 ): QuickBooks Pro 2009 free after rebate, with free shipping, all you pay is sales tax.  So I bought it, because QB 2000 is getting a little whiskery and beginning to exhibit the kind of weird problems you get with really old software on new hardware - for instance, claiming it does not have enough RAM to run, when it needs 2MB and there is only 3GB free.  :)  Codeweavers' site says QB Pro 2009 is not supported yet.  I'll try it out in Crossover anyway, but if it doesn't work I'll probably just vm it for a while until the support is there.

---

