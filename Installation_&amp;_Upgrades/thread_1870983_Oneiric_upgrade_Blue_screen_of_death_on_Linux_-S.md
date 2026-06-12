---
title: "Oneiric upgrade: Blue screen of death on Linux?? :-S"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Kermit524 on 2011-10-28
<update>
Checking out system settings => displays, I get: Driver: GeForce 9600 GT/PCI/SSE2
Experience: Fallback
Does this mean the system falls back to a very basic and limited graphic driver and not using the vendor's?
</update>

---

Hi, Before posting this, I have looked up recent posts, and in general all over the web, and realized many people are struggling with very similar issues, however, due to my lack of experience, I couldn't really relate to anything exactly similar to what I am having here, and I would rather avoid messing up with things less I make things worse. So here goes:

I have written here a very long tale of woe, but to make a long story short: I am probably having problems with my nvidia graphics hardware. What do I do: How do I control its driver - how do I know if I am using the propriatry dirver or the vendor's? how do I switch between the two? basically what do I do to make at least gnome to work properly with my graphic card again?

1. Upgraded my system from lucid to natty - got a message that my hardware is not compatible with Unity - fell back to Gnome - no problems. So I went ahead and most stupidly tried to upgrade to Oneiric. All went well untill login screen - no error messeges. So I simply logged in - and at that point I ended up with a slick blue empty screen with only the cursor.
2. I reset the X-Server (alt gr + prtscreen +k) and logged in again with classic gnome - here I get my desktop but with a very limited range of colors - basically - everyrhing from black to dark brown... With that - many icons are missing.
3. Only think that's sort-of working is KDE, but here too - I have color issues, some apps crash, some doesn't launch at all.

Any help would be appreciated. Many thanks in advance,
Michal

---

### Post by oscarivera9 on 2011-10-28
Not to worry, we are here to help.  However, in order for us to help you, we need for you to give us some information first.  As much information about the basics of your setup is the best you can give us.  What kind of PC, CPU, graphics card, how much RAM, that sort of thing.  Post that up and then we'll try to guide you through the process of getting everything working again.
If it makes you feel better, I also had an empty screen (mine was black with a flashing cursor) after upgrading from Maverick to Natty.  I now know what my problem was, and it was indeed hardware related.  So, if you want to save lots of time, re-installing Lucid (or Maverick if you want something newer) might be the way to go.  Otherwise go with my first suggestion.  Give us some basic information and we'll be better equipped to help you.

---

### Post by Kermit524 on 2011-10-28
Thanks for your help! Here's all the details that I can think may be relevant. Please let me know if anything missing:

System: Ubuntu 11.10 oneiric
Kernel Linux 3/0/0-12-generic-pae
GNOME 3.2.0

Hardware
Memory: 5.0
Processor 0-7: Intel(R) Core(TM) i7 CPU @9300 @2.67Ghz

Driver: GeForce 9600 GT/PCI/SSE2
VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] rev a1)

My screen is a DELL LCD - can't get any further details about it - the system declares it "unknown".

Another question: You suggested that I should reinstall a former version as the easy way out, but since both system files an user files are on the same partition - shouldn't this mean I have to start on a clean hard-disk?

Thanks again and in advance,
Michal

---

### Post by Kermit524 on 2011-10-28
So here's what I got up until now:
1. Apparently lightDM was not installed. I have installed it, and selected gnome as my default login. Now, at logging in with Unity, I get a black screen instead of blue...
2. With Gnome classic everything stays the same: a color range of 4-5 very dark colors/
3. I have tried to download and install gnome-3 and Unity-2d. In both cases - same color issues.
4. When I open a window, or a photo - the colors are ok. Same thing when I launch Windows on a virtual machine - graphic and colors are just perfect - same as before. So I know nothing is wrong with the hardware. Question still remains: how do I fix the driver problem?
Again - many thanks in advance for your help,
Michal

---

