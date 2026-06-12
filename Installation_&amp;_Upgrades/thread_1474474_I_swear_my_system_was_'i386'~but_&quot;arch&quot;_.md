---
title: "I swear my system was 'i386'~but &quot;arch&quot; command says i686?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2010-05-06
Hey friends..

 I didnt want to post this but I am really confused here...
(and IRC was too crazy to be very beneficial at the moment) lol

 When I first started using Ubuntu about 6 months ago...
I was sent the 9.10 CD, and that is what I used... and it worked great.

 For some reason, and at the moment Im not really sure why..
[edit: maybe because my processor is 2.2 GHz and I thought i386 was for slower machine?]
but I could have sworn that my PC was [i386 architecture] .hmmm
(doesn't that mean 'slower' pcs?) or am I mistaken?
{yea, im a noob, and dont know much about this at all} lol:mad:
I have been downloading these..
> ubuntu-10.04-desktop-**i386**.iso.torrent   as my discs~ 

and for the most part, everything seems to work great, 
except for a couple graphics issues on certain things..
but the system itself runs amazing. 

however,
I just learned the "arch" command, and tossed it into terminal..
and what came back is **i686** . 

So, Question1~
would a "i386" cd work ok on a "i686" machine?
[if im even using the terminology right]
but I dont think I am. lol

Q2~ Do you think that my minor "graphics card" issue(s)
would be fixed if I did download the "i686 CD?
I feel these are probably 'duh' questions with simple answers..
but I truly am confused. lol

When I had Karmic installed...
the only issue I ever had with it,
was that it would freeze once in awhile,
totally freeze and nothing would work but sysrq reisub to restart it. 

In 10.04 now, It doesnt freeze at all! ... 
however.. Once in a great while , like when Im posting on the forum,
all the sudden my PC will go blank, and start flashing a black background 
with white/grey vertical stripes on the top half of the screen...
and I cant get out of it unless i again, use reisub. 

 Trying to open stellarium does the same thing.

It doesnt happen often, 
and Im not posting to address those issues really, 
just giving examples... 
so maybe you could tell me if this "architecture" 
thing could be the root of these minor problems? 

Should I download the 10.04 i686 torrent and see what happens?
or am I just completely confused and all wrong here? lol:-k

 many thanks for any insight.

---

### Post by Rasa1111 on 2010-05-06
well... crap...
Now that Im looking again [I just looked 5 minutes ago I swear] here..
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
and I dont even see a i686 download now...(thought I did not long ago)
maybe im overtired..... man, I dont know... lol
such a fool... :lol:

where i got the command..
he also said..
> **arch**
Displays the processor architecture so I know if I should download i386,  i686 based application packages.

so only application packages? 
wth, am I going on over nothing? 
i think i might be.lol...           :(

---

### Post by howefield on 2010-05-06
> **Rasa1111 said:**
> and I dont even see a i686 download now...

You either need a 32 bit download or a 64 bit download.

i686 is 32 bit.

If you still have Ubuntu installed, try opening a terminal and look at the output of the command

```
cat /proc/cpuinfo
```

If you can see lm in the list of flags, your processor can run either 64 bit or 32 bit. If not, it can only run 32 bit.

---

### Post by lechien73 on 2010-05-06
The naming convention for Ubuntu releases is i386 for the 32-bit edition, and amd64 for the 64-bit edition. There is no i686 installation CD. So you just need to decide whether you install the 32-bit (i386) or 64-bit (amd64) editions. You have the 32-bit edition installed currently, which is fine.

If your processor and motherboard support it, and depending on the amount of RAM in your machine, you may get better performance by installing the 64-bit edition. My understanding is, though, that there's no direct upgrade path from the 32-bit to 64-bit editions - you would have to re-install.

With regard to your graphics card problems, it might be an idea to check the stickies at the top of this forum, and also [here]("http://ubuntuforums.org/showthread.php?t=1469475").

---

### Post by Rasa1111 on 2010-05-06
> **howefield said:**
> You either need a 32 bit download or a 64 bit download.

i686 is 32 bit.

If you still have Ubuntu installed, try opening a terminal and look at the output of the command

```
cat /proc/cpuinfo
```If you can see lm in the list of flags, your processor can run either 64 bit or 32 bit. If not, it can only run 32 bit.


 ahh thank you! 
excellent. 
yep, no ' lm' in the flags list.  
cool, so i *was* going on about nothing. :lol:
figures.  lol  :p

thanks allot, that is a good command to know. :KS+1
solved. 

edit: ohh yeah, I think I will always have Ubuntu installed from now on.. lol 
i cant imagine using anything else now. 
<3

---

### Post by Rasa1111 on 2010-05-06
> **lechien73 said:**
> The naming convention for Ubuntu releases is i386 for the 32-bit edition, and amd64 for the 64-bit edition. There is no i686 installation CD. So you just need to decide whether you install the 32-bit (i386) or 64-bit (amd64) editions. You have the 32-bit edition installed currently, which is fine.

If your processor and motherboard support it, and depending on the amount of RAM in your machine, you may get better performance by installing the 64-bit edition. My understanding is, though, that there's no direct upgrade path from the 32-bit to 64-bit editions - you would have to re-install.

With regard to your graphics card problems, it might be an idea to check the stickies at the top of this forum, and also [here]("http://ubuntuforums.org/showthread.php?t=1469475").

thank you lechian!
very good to know that. :)
good link to, thanks!
i appreciate it!

---

### Post by cascade9 on 2010-05-06
I know this is pretty much solved, just thought I should put this in- 

i386 is the architecture intel made for the 386 processors. A i386 distro will (OK, should) install and run on any 32bit x86 CPU (386, 486, 585, 686 or later). 

[http://en.wikipedia.org/wiki/Intel_80386](http://en.wikipedia.org/wiki/Intel_80386)

i686 (P6) is the architecture used on the Pentium Pro and later x86 CPUs. i686 will not install on 386, 486 and 586 CPUs- you need a pentium pro/pentium II or later Intel x86 CPU, or an Athlon or later AMD CPU (K5, K6, K6/2, K6/3 are still i586). 

[http://en.wikipedia.org/wiki/Intel_P6_%28microarchitecture%29]("http://en.wikipedia.org/wiki/Intel_P6_%28microarchitecture%29")

[http://en.wikipedia.org/wiki/List_of_Intel_CPU_microarchitectures](http://en.wikipedia.org/wiki/List_of_Intel_CPU_microarchitectures)

Arch used i686 as the lowest level architecture, so it reports as i686. ;) 

Hope that made sense ;)

---

### Post by Rasa1111 on 2010-05-06
Indeed it did, Cascade, thank you!! :D

---

