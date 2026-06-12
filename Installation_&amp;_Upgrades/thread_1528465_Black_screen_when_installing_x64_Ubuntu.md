---
title: "Black screen when installing x64 Ubuntu"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by lorgonjortle on 2010-07-10
Howdy!

I've been wanting to switch to x64 to get the most out of my hardware, but I seem to have run into some problems... Over the past three days I've been working diligently at trying to figure out why when I try to install 10.04 x64 I get a black screen with a blinking cursor... I think it's deeper than I had initially thought. A look at what I've done:

Since I thought it was just a graphics problem with Lucid, I tried changing the boot parameters. Here are some of the things I've tried (I'm sure I've tried more in my frantic periods where I just type things) to append after 'quiet splash':

```
nomodeset
```
```
nomodeset xforcevesa
```
```
xforcevesa
```
```
nomodeset xforceintel
```
```
xforceintel
```
```
i915.modeset=0 
```
```
i915.modeset=0 xforcevesa
```
```
i915.modeset=0 xforceintel
```
```
i915.modeset=1 
```
```
i915.modeset=1 xforcevesa
```
```
i915.modeset=1 xforceintel
```

Finally, being too frustrated to carry on with Lucid, I decided I'd stick with 9.10 x64. So after that finished downloading and I checked the MD5 sum (as I did with Lucid), I tried to install that... with no luck.

Here's exactly what happens for both of them:
I boot
The CD is booted
I am prompted with the main Ubuntu menu
If I choose anything other than to boot from the first HDD I'm presented with an eternal black screen with a blinking cursor.

Thinking that something must be going on under that black screen, I've tried removing 'quiet' and 'splash' from the boot parameters, but it changed nothing.

I was told that I should try a CD-R as opposed to the DVD+Rs I was using. I did so, but came to the same conclusion. In my last breath before coming here, I used Unetbootin with my ISO to create a bootable USB drive. I booted into it, and chose to continue with the setup... Surprise! Just a black screen with a blinking cursor.

I'm all out of ideas, and I'd love to read some of yours!

My computer specs (that you might need) are as follows:
Dell XPS 630i
Intel Core 2 Quad Q6600 @ 2.4GHz
nVidia GeForce 9800 GT
6GB RAM
500GB HDD

Thanks for any help!


EDIT: I've now tried the 10.04 alternate disc, too. The same problem occurred... I tried 'nomodeset' and 'i915.modeset=0' but nothing's working. I'd really appreciate some help; ot seems like a lot of people have this issue. One other way I'm trying is to extract the ISO and add the kernel boot as an option in GRUB.I doubt it'll change anything, but it's worth a shot. This must be an nVidia problem...

---

### Post by lorgonjortle on 2010-07-11
Bump

Has anybody solved this? I read in another thread somewhere that a dude unplugged his second (unused) HDD and it installed fine. I have three HDDs in my computer, and I'm only (really) only using one. I'll try unplugging then systematically, too.

Please help!

---

