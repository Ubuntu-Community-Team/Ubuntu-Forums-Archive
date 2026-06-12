---
title: "Issues with Lightning and Thunderbird 3.0?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2010-03-23
Does the Lightning calendar extension work with Thunderbird 3? Because I tried installing it, restarted Thunderbird and nothing. No notification of new plug-ins, no notification of incompatible plug-ins, no sign of anything in the program proper, not a thing.

Help?

---

### Post by lidex on 2010-03-23
Working fine here x64:
```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100316 Lightning/1.0b1 Thunderbird/3.0.3
```

---

### Post by Sslaxx on 2010-03-23
How bizarre. Nada this end. Hmmm. Tried running Thunderbird from the console no messages popping up that might provide clues. Thunderbird's internal error console also shows nothing.

---

### Post by lidex on 2010-03-23
Paste your "Help>About Thunderbird" data here.
32 or x64?

---

### Post by Sslaxx on 2010-03-23
32-bit.

[QUOTE="Help->About Thunderbird"]```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.8) Gecko/20100322 Thunderbird/3.0.3
```[/QUOTE]

---

### Post by lidex on 2010-03-23
As I suspected - it's not installed.

---

### Post by Sslaxx on 2010-03-23
Really. I'm pretty damned sure I've installed it - double-checked that with Synaptic.

Also, you're running 1.0b1 - the version I see in the repos is 0.9.

---

### Post by lidex on 2010-03-23
Go here:
[https://addons.mozilla.org/en-US/thunderbird/addon/2313]("https://addons.mozilla.org/en-US/thunderbird/addon/2313")
Right-click and save to your desktop. Open add-ons manager in T-bird, click the install button and navigate to that file.
You'll need to restart it to take effect.

---

### Post by Sslaxx on 2010-03-23
Will do. Thanks! Does appear that something is wrong with the version in the repos, then.

---

### Post by mlentink on 2010-03-23
AFAIK you do not install Lightning with synaptic. You install it from within Tbird as an add-on

---

### Post by Sslaxx on 2010-03-23
Except that *it's included in the Ubuntu Lucid repositories*, therefore you're supposed to be able to!

---

### Post by crjackson on 2010-03-23
I have it installed on 32bit, but I had to use the Addon manager to properly install.

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.10pre) Gecko/20100321 Lightning/1.0b1 Shredder/3.0.5pre
```

---

### Post by inveratulo on 2010-03-24
Unfortunately I am getting a different problem.  Anyone else had this?

and my mozilla about:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100316 Thunderbird/3.0.3

Looks like 64-bit is the only differentiating factor

---

### Post by lidex on 2010-03-24
> **inveratulo said:**
> Unfortunately I am getting a different problem.  Anyone else had this?

and my mozilla about:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100316 Thunderbird/3.0.3

Looks like 64-bit is the only differentiating factor

I had same problem - let me dig up the link for the x64 package.

---

### Post by lidex on 2010-03-24
Here you go. You'll need both packages:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/")

---

### Post by robfish on 2010-03-30
So how do you install those downloaded add-ons?

---

### Post by lidex on 2010-03-31
In Thunderbird go to "Tools>Addons", click the install button and navigate to the xpi files. Install gdata-provider first.

---

### Post by robfish on 2010-03-31
Thanks.
Before your reply I applied available updates and rebooted and then it worked (I had already tried your simple method without success).
I am currently trialing Ubuntu 10.04 Beta1 in Virtualbox.
Do you think that 10.04 final will have Thunderbird and Lightning all sorted out for 64bit?

---

### Post by lidex on 2010-03-31
> **robfish said:**
> Thanks.
Before your reply I applied available updates and rebooted and then it worked (I had already tried your simple method without success).
I am currently trialing Ubuntu 10.04 Beta1 in Virtualbox.
Do you think that 10.04 final will have Thunderbird and Lightning all sorted out for 64bit?

Of course. But it matters little to me as my install works fine.

---

