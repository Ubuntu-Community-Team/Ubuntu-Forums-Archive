---
title: "Wine not installing Photoshop CS2"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by nichpakaich on 2008-05-02
I've just spent hours (due to my lame internet connection) to download Photoshop CS2 trial because I planned to use Photoshop on my Ubuntu 7.10.

My problem is, I cannot install the program through wine. I did update my wine to the latest version for Gutsy (wine 0.9.59). And I tried many tips from users in this forum, but the setup just won't run.

If I double-click the "Setup.exe" from my file browser, an error dialog box is shown, telling 
> ".\AutoPlay\Main.ini"
"MAIN_FILE_VERSION"
"PRODUCT_REGISTRY_PARENT"
"PRODUCT_REGISTRY_KEY"

So, I try to run the "Setup.exe" from terminal, I typed
```
wine Setup.exe
```
then, (I think it's) a Splash Screen brought up, only it's blank. On the Title Bar it shows "Adobe Photoshop CS2". But after that, nothing happens. The terminal shows no error or whatsoever.

Any one got a clue to solve this? I'd be grateful :(
PS: I do know that wine-doors provide useful service regarding this, but if I should encounter another waiting (for the downloading), I think I'll waste my time.

---

### Post by empthollow on 2008-05-02
i don't know specifically how to solve this but the most useful information i've found about running progs under wine is at [www.winehq.org](www.winehq.org) in the app database.  type photoshop in the search and there will be a list of people who tried what versions of photoshop and wine and what worked and what didn't.

---

### Post by nichpakaich on 2008-05-03
> **empthollow said:**
> i don't know specifically how to solve this but the most useful information i've found about running progs under wine is at [www.winehq.org](www.winehq.org) in the app database.  type photoshop in the search and there will be a list of people who tried what versions of photoshop and wine and what worked and what didn't.

thanks for the info, I did what you told me, and still I get stuck. Got additional message:
> fixme:ole:DllRegisterServer stub

now what?:confused:

---

### Post by Slim Odds on 2008-05-03
> **nichpakaich said:**
> thanks for the info, I did what you told me, and still I get stuck. Got additional message:


now what?:confused:

Use GIMP

---

### Post by nichpakaich on 2008-05-03
> **Slim Odds said:**
> Use GIMP

I still in need of Photoshop Blending Options, etc. Tried to get familiar with GIMP, too. But the needs just need to be fulfilled :(

---

### Post by empthollow on 2008-05-03
the reason gimp doesn't have the blending options is because adobe has them patented. Gimp will do all of the things that photoshop does with the blending options it just takes alot more steps.  That being said, I have successfully run photoshop 7 and cs successfully under wine without issue.

---

### Post by Slim Odds on 2008-05-03
> **empthollow said:**
> the reason gimp doesn't have the blending options is because adobe has them patented. Gimp will do all of the things that photoshop does with the blending options it just takes alot more steps.  That being said, I have successfully run photoshop 7 and cs successfully under wine without issue.

LOL   you can't patent an idea. You can patent the algorithms, but not the concept.

---

### Post by nichpakaich on 2008-05-04
Okay, I got it running fine now :D
The solution? Arr.. it's my bad, actually, I access the wrong folder.
In the "Photoshop CS2" folder, there is a "Adobe(R) Photoshop(R) CS2" .. and THAT is the folder that contains the right "Setup.exe" :lolflag:

---

### Post by empthollow on 2008-05-05
> **Slim Odds said:**
> LOL   you can't patent an idea. You can patent the algorithms, but not the concept.

You know, i questioned that a little when i wrote it but i swear i read that when i was looking for something like blending options for gimp.  Must have been somebody making up stuff.

---

