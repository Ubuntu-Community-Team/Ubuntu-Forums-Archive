---
title: "Oneiric 11.10 and kde3 libs ??"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by eldon.t on 2012-03-19
Hi,

i've upgraded by mistake my ubuntu 11.04 to 11.10, a few days ago and i'm discovering that kde3 libs have been ditched, thx very much.

i need them to build my kaffeine 0.8 version. I don't wan't to use the available kaffeine 1.2 which is a serious downgrade from the 0.8 branch, features wise.

I'd like to know if there's a how to guide to get back kde3 libs on oneiric.
I could build them myself if necessary but i like to use repos / packages as much as i can of course..

I'm currently trying to use trinity desktop ppa and packages but so far no luck, i don't know if their kde3 sources are modified or not and if they would work on vanilla kde3 apps sources, i'll ask them about that but if you already know..

The best thing would be to get back some ../kde3/.. libs paths into the system so old kde3 apps would find them easily but i'm not sure how to accomplish that and i don't want to completely break down my kde libs as i'm also using other kde apps that are not using kde3 libs anymore..

thx for reading, all comments and info will be greatly appreciated.

---

### Post by netandif on 2012-04-11
why don't you simply adjust your kaffeine source to point to the trinity paths and then compile?

---

### Post by eldon.t on 2012-04-11
not sure what to respond to that, but that's "configure" jog to figure out what is where..

Trinity using custom paths, you have to tell configure where to look and then it finds the headers and libs as it should.
Unfortunately once you start compiling the source it fails but not with "code errors" but lib (functions) references errors.

I don't understand why that happens, i don't know if all trinity apps sources are tainted to use trinity kde3 libs, i doubt that but haven't checked kaffeine-trinity sources yet..

i'm busy porting some of my patches to kaffeine 1.2 and trying to bring back some kaffeine 0.8 goodies in there.
I can't say my kaff 1.2 will ever be as good as 0.8 was, there are some interesting pros in 1.2 but also some serious cons..

---

### Post by tim__b on 2012-05-10
Same problem here with Precise. Trying to get kaffeine 0.8.x to compile...
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
make: *** [debian/stamp-autotools] error 1

```Has anyone been able to patch 0.8.x sources to work with kde4 libs?

---

### Post by eldon.t on 2012-05-13
kaff-08 won't work with kde4 libs

after failing to build my kaffeine 0.8 source against trinity (kde3 port) libs, i stopped looking and started to patch kaff 1.2.2

I should mention that their kaffeine-trinity (0.8.8) package did work on my 11.10, but i couldn't get my sources to build.
Not sure trinity is already ported to 12.04, i've read some messages on their mailing list asking for 12.04 status..

---

