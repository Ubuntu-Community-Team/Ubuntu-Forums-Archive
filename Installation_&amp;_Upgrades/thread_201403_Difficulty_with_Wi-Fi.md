---
title: "Difficulty with Wi-Fi"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by master_runner on 2006-06-21
I've decided that this better fits the installation forums rather then the Wi-Fi forum, as it seems to be am issue of just everything being screwed up.

so, here's my tale of woe:

I just installed Ubuntu Dapper Drake on my laptop, a Dell Inspiron 2200.
the difficulty started when my Broadcom DCM4318 WLAN card failed to function.
so, after a moment of thought, I determined I needed new drivers. so, off I went to searching these forums, from which I found that I needed the DCM43xx-fwcutter package. however, after multiple attempts to install this, I failed. horribly. so, anyway, I gave up on that and decided to install NdisWrapper. from the install instructions, it seemed pretty straitforward, just some cut'n'paste terminal work. anyway, I decompress it on my desktop, and I CD to it and enter into the console "sudo make install."
after entering my root pass, it indicated that "make" didn't exist, so I went off to install make. I then downloaded make 3.81, and began following it's installation instructions. this is where I ran into trouble. I CD'd there and entered "./install", as instructed by the install instructions. the sytem runs for ~3 seconds, and then prints the following: 
"configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details."
so, from this I conlude I need to install a C compiler. at this point I feel like I'm stuck in some kind of horrible computer purgatory, and I'll be circling around like this for the rest of my life. so, my question is, do I just neeed to install a C compiler, and if so where can I find one, and why doesn't ubuntu include one by default? or, do I not need a C compiler, and I'm just doing something wrong?

thanks,
MR

---

