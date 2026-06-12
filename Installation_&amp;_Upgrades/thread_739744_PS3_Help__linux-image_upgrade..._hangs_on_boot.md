---
title: "PS3 Help :: linux-image upgrade... hangs on boot?"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by ninjaschwa on 2008-03-30
I've had a quick search of the forums but can't find anythig along the lines of my problems...

Basically I'm running Ubuntu Feisty 7.04 on my PS3 and I've ticked and installed with Synaptics; linux-image-powerpc-smp 2.6.20-16, previously installed was 2.6.20-15 (and I think it still is...?) then my upgrade manager told me I needed to restart; so I did...

Now it won't boot, I get my kboot prompt and hit enter as usual, it says 'loading initrd' or what not, then it says 'booting kernel' and then it hangs, and shuts off totally with only the red LED still lit... even if I type 'old' or 'linux single' I get nowhere it still hangs at 'booting kernel'...

I'm stumped... if it was kernel then I would be able to boot using 'old' or recover using 'linux single' right? So all I can see it being is the kboot is out of date maybe? I'm not particularly fussed on having the new linux-image or any of the newer ones, I only upgraded since the numbers were higher... stupid reasoning I know :P

Any help is muchos appreciated?
Cheers fellas!

---

### Post by ninjaschwa on 2008-03-30
Hi again guys... double posting to smooth out a few bits from the original post, sorry it was late (read: very early) by the time I got to bed last night trying to fix this... anyway here's my errors...

Boot in fact hangs on ''Booting system...''

I haven't upgraded linux-image I don't think I've found the packages again on the Synaptics on the LiveCD, I've installed...

linux-restricted-modules-powerpc-smp version is 2.6.20-16 or there abouts... and,

linux-restricted-modules-2.6.20-16-powerpc-smp

Seeing as my kboot is dying no matter what I imput I assume these have some how knackered my bootloader, can I re-download otheros.bld, an updated one, and then re-install that on the XMB? Would that work or would I then need to re-install Ubuntu aaaaall over again? I mean, that's not *such* a bad thing since I could get 7.10 over 7.04 however I don't have much of a means to back everything up via mounting the disk on the LiveCD... sorry for the bump as it were, again, help appreciated :)

---

