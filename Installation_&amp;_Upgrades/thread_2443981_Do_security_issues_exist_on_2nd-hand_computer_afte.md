---
title: "Do security issues exist on 2nd-hand computer after Erase Disc install?"
date: 2020-05-22
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2020-05-22
I received a Dell Inspiron laptop from a stranger who gave it to me instead of throwing it away.  I successfully installed Lubuntu 20.04 using the Erase Disc method with the installer.  

I'm wondering if there are any possible security issues related to using this laptop now.  (For example, could someone set up a HDD so that it had an un-erasable partition that included a program with keylogger or something.  I have no idea if that's possible.  Just imagining....)  If so, is there anything I can do to mitigate/remove those possible security issues?

Thank you.

---

### Post by DuckHook on 2020-05-23
The devil is in the details.

There are UEFI nasties that can hide in your system BIOS. HDD nasties can now hide far beyond the old boot sector/partition sector areas&#8212;they now hide within the HDD/SSD firmware itself. To my knowledge, few if any antimalware apps can detect stuff like this.

That's on the paranoid side. On the bright side, old laptops are donated to schools and nonprofits all the time. They find a good second home and don't become another article of e-waste toxifying our landfills. This is a good thing.

I'm not trying to either alarm you or reassure you. Danger exists, but so does generosity. Like all things in life, we have to measure probabilities, risk tolerances and the context of any given situation and then make a personal decision.

---

### Post by guiverc on 2020-05-23
All my hardware is either donated to me, or purchased second hand from re-cyclers.

Assuming I don't change the hardware (change graphics card, put in different drives etc), all I usually do is what you've already done - ie. re-install the OS (including one that came with pre-installed with a Ubuntu too).

I have for some devices (eg. a family given ipad) setup so network traffic was recorded for me to later examine (traffic being sent to? how often? size of traffic? etc, mostly just wireshark with limited analysis really), but that was more out of interest than suspicion.

---

### Post by anotherChris on 2020-05-25
> **DuckHook said:**
> The devil is in the details.

There are UEFI nasties that can hide in your system BIOS. HDD nasties can now hide far beyond the old boot sector/partition sector areas—they now hide within the HDD/SSD firmware itself. To my knowledge, few if any antimalware apps can detect stuff like this.

That's on the paranoid side. On the bright side, old laptops are donated to schools and nonprofits all the time. They find a good second home and don't become another article of e-waste toxifying our landfills. This is a good thing.

I'm not trying to either alarm you or reassure you. Danger exists, but so does generosity. Like all things in life, we have to measure probabilities, risk tolerances and the context of any given situation and then make a personal decision.


> **guiverc said:**
> All my hardware is either donated to me, or purchased second hand from re-cyclers.

Assuming I don't change the hardware (change graphics card, put in  different drives etc), all I usually do is what you've already done -  ie. re-install the OS (including one that came with pre-installed with a  Ubuntu too).

I have for some devices (eg. a family given ipad) setup so network  traffic was recorded for me to later examine (traffic being sent to? how  often? size of traffic? etc, mostly just wireshark with limited  analysis really), but that was more out of interest than  suspicion.


Okay, thank you both.

---

### Post by kurt18947 on 2020-05-25
Now that you have it set up I don't know if I'd do it now but I've run [DBAN (Darik's Boot and Nuke)]("https://www.lifewire.com/how-to-erase-a-hard-drive-using-dban-2619148") on hard drives of uncertain history. I gather DBAN is not optimal for SSDs. [Here's an article]("https://grok.lsu.edu/Article.aspx?articleid=16716") about an alternative that seems like it may be more suitable for solid state media.

---

### Post by TheFu on 2020-05-25
> any possible security issues
That's a pretty huge list of possibilities.   There are hundreds. But whether any of those are likely is a completely different question.  

Why did you get the free laptop?  Have any parts been replaced?  Which OS did it run before you got it?  Do you work for a non-profit or NGO or govt or as a contractor for any of those organizations?  Are you trying to subvert any govts?  if you were walking it work and someone "gave you" anything outside a specific building, that can mean all sorts of bad things.  Normally, they'd just drop 10 flash drives in the parking lot to gain internal network access - or send a free new keyboard or other USB device to the CiO.  Everyone likes free stuff.  ANY USB device can be used to take over any powered on computer due to the way drivers are auto-loaded.

BTW, I&#8217;m typing on a used laptop now, purchased off ebay.  it was a random purchase (don't buy much from ebay) and the seller had about 500 similar off-lease laptops for sale.  Non-random purchases may be a concern.  
Previously, i have walked into an office equipment store, pulled a random chromebook from the shelf, paid cash for it at the register, never used any google accounts with it for about a month, then broke the firmware phyiscal DRM on it, replaced the firmware/BiOS and loaded an ubuntu-version to be used for about 3 yrs.  Of course the system was encrypted w/ 2FA required to unlock it. ;)

But people say I&#8217;m a little cautious.  Just depends on the risks for your situation.

---

### Post by QIII on 2020-05-25
Saying that DBAN is "not optimal for SSDs" falls short.  It simply does not work.  An SSD is a completely different beast.  From Dban.org:  ".. It cannot detect or erase SSDs ..."

The factory reset described in your linked article is the way to go, as it makes sure that all erasure blocks are cleared.  It looks to me like they may have sourced that article in large part from [this article]("https://wiki.archlinux.org/index.php/Solid_state_drive/Memory_cell_clearing") on wiki.archlinux.org.

---

