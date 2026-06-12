---
title: "boot 12.04 from cd problem"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by Dominic Waldron on 2012-06-18
I downloaded Ubuntu 12.04, wrote to disc and installed it on Dell PC 

Then I tried to install on IBM T41 Laptop.

I got this message.....

"Unable to boot-please use a kernel appropriate to your CPU"

Any ideas what should I do now?

---

### Post by Rex Bouwense on 2012-06-18
After a quick google search I found minor problems with installation to the IBM T41 Laptop but nothing like you describe.  How old is the lappie and how much RAM have you got?  Perhaps it doesn't have the guts to run 12.04.

---

### Post by steeldriver on 2012-06-18
you may need a non-pae kernel - afaik for 12.04 that means you will need to install from the mini-iso

[http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

---

### Post by sudodus on 2012-06-18
Lubuntu (and I think also Xubuntu) 32-bit versions of 12.04 are non-pae by default.

I beta-tested it on an IBM T41, and it works very well for me, except that the default video player, mplayer2, does not work. But I downloaded vlc, and it works (as well as can be expected on that hardware).

---

### Post by Dominic Waldron on 2012-06-18
Thanks Rex, It must be at least five years old.  2GB RAM. 120GB hard drive. Running Windows Vista on 20GB partition, Ubuntu 11.04 on 15GB partition and Shared Data partition using the rest. No problems at present but I thought it was about time to run the latest Ubuntu.

---

### Post by Dominic Waldron on 2012-06-18
Thanks to everyone. 

I just tried the disc again and found the beginning of the error message reffered to pae.

Then I found this....

[http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

I'll give it a try tomorrow but I need to sleep now.

---

### Post by Dominic Waldron on 2012-06-18
Steeldriver. I just noticed you had already mentioned that link. Thanks.I missed it due to it being the middle of the night here and me rather befuddled with tiredness.

---

### Post by sudodus on 2012-06-19
The easiest way to get a new system for an IMB T41 is to choose another flavour of Ubuntu: Lubuntu or Xubuntu. These are distributed via iso files with non-pae systems, *and* they use light-weight desktop environments, so that they work better on slow computers with small RAM.

But you can also install standard Ubuntu with Unity or Gnome 3 starting with the mini-iso, or via upgrading from an older version.

---

### Post by steeldriver on 2012-06-19
> **sudodus said:**
> Lubuntu (and I think also Xubuntu) 32-bit versions of 12.04 are non-pae by default.

oops, I should have known that - I'm using Xubuntu on several machines but they're still at 11.10 and I haven't really looked at the 12.xx upgrade path

fwiw my older laptop is a Thinkpad X30 which is about the same vintage as the T41 (1.2GHz PIII-M) I've got that dual booting with Xubuntu and CrunchBang at the moment - I'd definitely recommend looking at the lighter *buntus like sudodus said

---

