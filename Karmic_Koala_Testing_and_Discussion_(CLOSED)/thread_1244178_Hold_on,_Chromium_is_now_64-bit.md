---
title: "Hold on, Chromium is now 64-bit"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-08-19
I just noticed with the latest build from the PPA (23670) that Chromium is 64-bit native. This means it has all plugins, including Flash, working.

This is some rapid application development.

---

### Post by steeleyuk on 2009-08-19
Just upgraded to Karmic and installed 64-bit Chromium. Nice to see it can import Firefox data/settings as well (not sure how long its been able to do that).

---

### Post by b3n87 on 2009-08-19
google need to get it ready for Chrome OS :D

But yeah, they really are setting up their game on the speed of development!

Kudos

---

### Post by ihendley on 2009-08-19
I just installed 23670 and it doesn't appear to be 64 bit. My 64-bit plugins from ff are not working with it, but when I install the 32-bit versions they work fine.

How do I check whether I have the 64-bit version?

If I don't, then how to get it?

Thanks.

---

### Post by Moop on 2009-08-19
I just upgraded to 23670 and copied the 64 bit libflashplayer.so into /usr/lib/chromium-browser/plugins and then added
 --enable-plugins to the command to start chromium and it works great!

I never had the 32 bit plugins installed. 

Chromium is blazingly fast compared to FF (with all my extensions)

---

### Post by xebian on 2009-08-19
That's why the ia32-libs-chrom.. were removed.  

It's awesome.  Just watching YouTube in HD in it's own window. :guitar:

To check if it's:

rename the libflash in your chrome/plugins directory to something.so

Then type in the URL box about:plugins.  Yous should not see that something.so

---

### Post by xebian on 2009-08-19
> **Moop said:**
> I just upgraded to 23670 and copied the 64 bit libflashplayer.so into /usr/lib/chromium-browser/plugins and then added
 --enable-plugins to the command to start chromium and it works great!

I never had the 32 bit plugins installed. 

Chromium is blazingly fast compared to FF (with all my extensions)

Actually you don't need that plugins directory anymore as it reads it from the FF or mozilla locations.

---

### Post by froggyswamp on 2009-08-19
about : plugins also says Java is supported but it's not.
The 64 bit version is also slower in both sunspider and google's benchmarks.

ps: so far it's also buggier than 32 bit version, switching back, but can't wait for the final stable release!!

---

### Post by jppr on 2009-08-19
> **froggyswamp said:**
> about : plugins also says Java is supported but it's not.
The 64 bit version is also slower in both sunspider and google's benchmarks.

ps: so far it's also buggier than 32 bit version, switching back, but can't wait for the final stable release!!

who need stable version? :popcorn:

---

### Post by ghindo on 2009-08-19
When is Chromium supposed to end up in the Ubuntu repositories, again?

---

