---
title: "latest Adobe flash plugin"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mick222 on 2009-10-13
I just noticed on adobe's site that there is a more up to date flash plugin than the one in the repositories, will it be added soon or should I download it from the site.

---

### Post by emarkay on 2009-10-13
All I can say is I did that a few days ago and it TRASHED flash; I had to manually delete all files and directories of flash.

I'd use the repos till the RC is stable...

---

### Post by forumache on 2009-10-14
> **mick222 said:**
> I just noticed on adobe's site that there is a more up to date flash plugin than the one in the repositories, will it be added soon or should I download it from the site.

the flash packet you need is flashplugin-installer.
It will download the latest plugin from adobe.

---

### Post by Saneless on 2009-10-14
That depends on what you're running.. 32 or 64 bit?  If you're running 64 bit, the one in the repos is complete garbage, you'll want to get the alpha from Adobe.

---

### Post by zika on 2009-10-14
> **saneless said:**
> that depends on what you're running.. 32 or 64 bit?  If you're running 64 bit, the one in the repos is complete garbage, you'll want to get the alpha from adobe.+1.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz). Extract libflashplayer.so and put it in ~/.mozilla/plugins where it belongs and put it with Your  permissions not with sudo. Create plugins directory if it doesn't exist.  That is the proper place for user-installed plugins.

---

### Post by forumache on 2009-10-14
> **zika said:**
> +1.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz). Extract libflashplayer.so and put it in ~/.mozilla/plugins where it belongs and put it with Your  permissions not with sudo. Create plugins directory if it doesn't exist.  That is the proper place for user-installed plugins.

only if mick222 runs 64bit, we don't know yet.

---

### Post by zika on 2009-10-14
> **forumache said:**
> only if mick222 runs 64bit, we don't know yet.Yes You're right, I was too quick on my keyboard. I assumed I've seen that he is on 64, but now I am not so sure anymore. My apologies.
(OP is using 64 bit as stated in another thread of his ... that is where I've picked that info ...)

---

### Post by mick222 on 2009-10-18
sorry I didn't reply decided to stick with the one in the repos for now. Might install it once Karmic is released . I am running 32bit had 64 bit intrepid and didn't like it much easier to configure 32bit and I only have 512mb ram/

---

