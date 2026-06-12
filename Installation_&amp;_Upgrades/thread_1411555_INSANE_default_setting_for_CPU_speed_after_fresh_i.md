---
title: "INSANE default setting for CPU speed after fresh install"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by asbesto on 2010-02-20
Ok, after dealing for months with slowness on my thinkpad T40, my desktop computer and another thinkpad T41, after trying TONS of fixes about Xorg (that now munch 40% more CPU than the Xorg of 2 years ago, and they have BROKEN the support for ATI CARDS, that was perfectly working, with stupid and obscure options like HEURISTIC GREEDY, but this is another story), after trying Opera, Chrome, the new Firefox and so on...

I just went to check the speed of my CPU.

Note: Laptops and Desktop works with AC adapter plugged every time. So, as is normal to be, I expect to have my CPU pushed to work 100%. Because I want to listen to MP3 without glitches, I want to see a movie without losting frames, I want to play games fluidly, as the 100% of the people out there.

And is NOT. 

And this is how my Centrino 1500 works with the new ubuntu FRESH install:

:frown:](*,)=D>
```

  current CPU frequency is 600 MHz (asserted by call to hardware).

```

:shock::shock::shock:

The fix is simple - installing cpufreq-governor stuff and so on. But the real problem is: Why such an INSANE default setting?

The computer is plugged to AC, so it's normal to set the cpu at 100%, not in "on-demand" mode!!! This make the computer REAL, REAL SLOW!

 ](*,)

I also checked my other computer, in which I was suffering slowness from month: et voila', the cpu setting is "ON-DEMAND", at 600 MHz instead of 1500.

 ](*,)

Really I don't understand WHY this. I hope this can help many people with slowness problems!

---

### Post by mkvnmtr on 2010-02-20
Is that not a bios setting apart from the OS

---

### Post by jocko on 2010-02-20
> **asbesto said:**
> ...
The computer is plugged to AC, so it's normal to set the cpu at 100%, not in "on-demand" mode!!! This make the computer REAL, REAL SLOW!
...
I also checked my other computer, in which I was suffering slowness from month: et voila', the cpu setting is "ON-DEMAND", at 600 MHz instead of 1500. ...

"on demand" means the cpu switches to a lower frequency when it is not being used much, but will instantly switch to a higher frequency when it's needed. I have always used "on demand" on my laptop to save battery, keep the cpu cool and the fan quiet. I have never noticed any slowdown because of this (as soon as I start something that uses more cpu the frequency of one or both of my cores ramps up from 1GHz to 1.33 or 1.83, without any noticeable lag).

If your cpu is set to "on demand" but is still locked to the lowest cpu frequency (or if it doesn't switch instantly when needed) there must be something wrong somewhere, either in whatever kernel module is responsible for the frequency scaling, or something specific to your bios, motherboard or cpu.

---

### Post by asbesto on 2010-03-10
I know it's something wrong - and, "on demand" is slow like hell, because it slow the cpu when possible. I'm plugged into AC -> I want 100% speed. That's the normal behaviour for users! 

it's unbelievable! :(

---

### Post by me13221 on 2010-03-31
> **asbesto said:**
> I know it's something wrong - and, "on demand" is slow like hell, because it slow the cpu when possible. I'm plugged into AC -> I want 100% speed. That's the normal behaviour for users! 

it's unbelievable! :(

I quite disagree.  As a user, I want my computer to use the resources it requires and not just dump my dollars and cents into its heat sink.  ondemand is the correct default.

I agree with the other posters-- if you are having performance problems (it's okay, it happens to everyone sometimes lol), it's not 'ondemand's fault.

---

### Post by 98cwitr on 2010-03-31
I kind of have the same problem. I'm OC'd to 3.6, but cpuinfo only will go to 3.2 :/

[http://ubuntuforums.org/showthread.php?t=1400474](http://ubuntuforums.org/showthread.php?t=1400474)

---

