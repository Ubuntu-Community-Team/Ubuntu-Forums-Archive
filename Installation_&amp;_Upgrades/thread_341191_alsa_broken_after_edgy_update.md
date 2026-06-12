---
title: "alsa broken after edgy update"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by Thymidity on 2007-01-18
Hi,

When I was using the live CD and just after I installed Ubuntu, I had two devices listed in sound control. One was an ALSA device and the other was Generic ... OSS. Now after I ran the update, I lost the ALSA one and with it the left channel of my headphones and the ability to switch between my laptop speakers and my headphones.

When I run 'alsamixer' I get 'alsamixer: function snd_mixer_load failed: Invalid argument'

I tried reinstalling the ALSA packages I found in Synaptic but that didn't solve my problem.

Should I be trying to fix ALSA or should I be trying to manually load the driver that I had before? I don't enough about Linux to know for sure whether or not ALSA is broken.


Thanks

---

### Post by Thymidity on 2007-01-18
After some more searching I found that I probably could fix it by installing Alsa 1.0.13 from source. I also found that my alsamixer comment was of absolutely no use (although, that's a pretty odd invalid argument message.)

I really don't want to install build-essential just to get sound. It's really just a matter of principle, now.

Does anyone know of a way to fix Alsa without having to run the newest non-Ubuntu version?


Thanks

---

### Post by Theimon on 2007-01-18
Don't have a solution for your problem but I am curious why you don't want to install build-essential though........those programs are kinda....well...essential. Or you just keep your Ubuntu as it is and never install anything?

---

### Post by Thymidity on 2007-01-18
Like I said, it's just a matter of principle. You shouldn't _have_ to install compilers, even though there's many reasons why you might _want_ to.

I'll check out the live CD when I have some more time and figure out this mess and get it fixed. I just wanted to see if someone had a quick solution.

Supposedly other people have had much worse problems with this sound card and had to work hard just to get the level of support I have now, so I should thankful. It's just that, I had it working much better, then, it was taken away from me --- I know it's available, I just don't have it.

I'll post when I fix it in case anyone else has similar problems.

---

