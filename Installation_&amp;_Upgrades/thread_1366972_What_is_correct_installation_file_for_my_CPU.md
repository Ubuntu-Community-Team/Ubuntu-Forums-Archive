---
title: "What is correct installation file for my CPU?"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by TJGeezer on 2009-12-29
I did a test install using Wubi Wubi and all went well, except my graphics chip on this low-end machine isn't supported. So I uninstalled and am waiting for a new card to arrive before I give it another go.

My question is:

With Wubi I got two installation files:
- mssefullinstall-amd64fre-en-us-vista-win7
- mssefullinstall-x86fre-en-us-vista-win7

My CPU is Intel Core2 Quad CPU Q8200 @ 2.33GH
I'm stuck running Vista 64 (see why I'm eager to get Ubuntu working?)

Wubi, in my trial run, installed the amd64 package not the x86 package.

Should I override this selection (make the amd file unavailable) or was it the correct one?

Simple question.... hoping it's a simple "use the defaults" answer with maybe a hint on why the amd64 package is the right one for this machine.

Thanks!

---

### Post by lloyd_b on 2009-12-29
> **TJGeezer said:**
> I did a test install using Wubi Wubi and all went well, except my graphics chip on this low-end machine isn't supported. So I uninstalled and am waiting for a new card to arrive before I give it another go.

My question is:

With Wubi I got two installation files:
- mssefullinstall-amd64fre-en-us-vista-win7
- mssefullinstall-x86fre-en-us-vista-win7

My CPU is Intel Core2 Quad CPU Q8200 @ 2.33GH
I'm stuck running Vista 64 (see why I'm eager to get Ubuntu working?)

Wubi, in my trial run, installed the amd64 package not the x86 package.

Should I override this selection (make the amd file unavailable) or was it the correct one?

Simple question.... hoping it's a simple "use the defaults" answer with maybe a hint on why the amd64 package is the right one for this machine.

Thanks!

IIRC, the "amd64" package handles all 64 bit processors, Intel and AMD alike.  So that would be the the correct package for your machine.

Lloyd B.

---

### Post by lukeiamyourfather on 2009-12-29
> **lloyd_b said:**
> IIRC, the "amd64" package handles all 64 bit processors, Intel and AMD alike.  So that would be the the correct package for your machine.

Lloyd B.

That's correct, amd64 is for both AMD and Intel 64-bit processors. Its called amd64 because AMD created the architecture. Intel adopted it and uses it as well in their 64-bit processors.

EDIT: Here's some history on it if you're curious.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by garvinrick4 on 2009-12-29
Like was stated use the 64 bit it automatically installs. I have 1 install of Wubi that I started
with and it is still on a Vista machine. You should though download the 64 bit .iso version to desktop and then BURN to Cd. 
 Do not have to boot to CD after that just stick Cd it tray and select Wubi and takes about 12 minutes or so to install. Always nice to have that Live CD around.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


alternatives download will have 64 bit.

---

### Post by TJGeezer on 2009-12-29
All good info - much appreciated!  I'll check the wikipedia links and will take the advice to grab the ISO. 

Responsiveness here is wonderful. Once I get back into using Linux maybe I'll be able to help somebody else. A great community, this.

Just think - not one person here called me a "Vis7ard"... a nice surprise.

TJ

---

