---
title: "If your live CD won't boot, and you have an nvidia card..."
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2008-04-24
I've spent the last few hours trying to figure out why my Live CD of 8.04 would not boot. It started to boot and then sent me to a screen full of distorted green and white lines.

Then it suddenly occured to me. I had my monitor plugged into my video card, and nvidia can cause problems.

So, I went to BIOS and reverted back to my onboard intel chipset, and woila! It worked! I'm now installing Hardy, and I'm excited!

So, if you've had this problem, give this workaround a try! :guitar::guitar::guitar:

---

### Post by cerpin on 2008-04-24
Alright I'm having the same problem you did, but I am not so BIOS savvy, could you help me out a bit? lol

I'm just not sure what it is i need to change.

---

### Post by Dynamo_Joe on 2008-04-25
Boot the Live CD and select "Safe Graphics Mode" and click on "Instal" after you've booted into the "live environment". 

Same with "Fiesty", "Gutsy", ..., yes, I have a Nvidia card ...

---

### Post by Unterseeboot_234 on 2008-04-25
I had to toss my first two CD-R into the trash. I couldn't quite burn 697meg onto CD. Tried a DVD-R+ and I have a LiveCD. AMD64 Hardy. Boots fine with a nVidia GE7500 series.

The reason I downloaded the upgrade was the release announcement touted Xorg wasn't such a big configuration ordeal, and Screen Resolution was selectable. I went into System --> Administration --> Screens and Graphics and... Hardy's idea of 800 x 600 is my idea of what 480 x 320 would look like on a Billygatebox. So, I'm posting my experience to find this thread again to see what others will accomplish with nVidia hardware.

But... this Hardy release really looks fabulous! More people would try Linux if the street price of Vista wasn't $8.00.

---

### Post by bg1256 on 2008-04-25
> **cerpin said:**
> Alright I'm having the same problem you did, but I am not so BIOS savvy, could you help me out a bit? lol

I'm just not sure what it is i need to change.

When you first power on your computer, you should see the manufacturer's screen with a few options. Look for one that says something like "setup."

On my HP, setup is the option that needs to be chosen, and then search around for the default video output option. I went in and selected "onboard," then switched my monitor to the onboard output.

Then, things worked. I still haven't had time to fuss with the nvidia stuff, so I'm working with onboard graphics, however.

---

### Post by Smudger on 2008-04-25
> **bg1256 said:**
> When you first power on your computer, you should see the manufacturer's screen with a few options. Look for one that says something like "setup."

On my HP, setup is the option that needs to be chosen, and then search around for the default video output option. I went in and selected "onboard," then switched my monitor to the onboard output.

Then, things worked. I still haven't had time to fuss with the nvidia stuff, so I'm working with onboard graphics, however.

Excellent, I had a problem with my Nvidia graphics card when I upgraded to 8.4, this seems as if it may be the solution I need.

---

### Post by pancakelizard on 2008-04-25
what do you do if you're in my situation and don't have an onboard video card and an nvidia card is your only output and all you want to do is run the live cd for awhile to see how you like it before installing it?

---

### Post by Ken Jannot on 2008-04-25
Is this the problem if NOTHING happens after I click "Install" (or any of the other choices, for that matter)? (I have an NVidia card.) Or have I just burned a bad CD? I tried the above suggestion of switching to safe graphics mode, but that changed nothing. Haven't yet tried the onboard card--thought I'd ask first.

---

### Post by c60 on 2008-04-25
Ran into the same issues, made three new coasters... switched over to the alternate cd iso and all works as expected.

btw : speaking to the 64bit iso

-- ran into the same problem with the kubuntu 64bit iso set as well...

very odd : never had an issue in the past couple of years.

/rb

---

