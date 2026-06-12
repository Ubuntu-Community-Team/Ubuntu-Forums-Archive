---
title: "Try Lubuntu Install"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by devilriderman on 2020-06-05
Hi,

Attempted to give Lubuntu a try, without installing.  I've read in a few forums that you need install the Desktop Version.  lubuntu-20.04-desktop-amd64.iso  I have a 64 bit Lenovo Ideapad 110, with AMD. I also tried the same with Lubuntu 19(.04?)  same result.  Gives them install options page with no "try Lubuntu without installing"

Thanks,
Ralph

---

### Post by guiverc on 2020-06-06
I'm sorry, but I don't understand your issue.

Yes you can try Lubuntu without installing, and it works.

However it's not perfect (nothing is), I just experienced a fail on a Lubuntu groovy 'live' QA-test because the write to the install media failed, which is not Lubuntu's fault, just a media failure (for whatever cause, likely another thumb-drive is near it's EOL)

To ensure a good result, I firstly validate ISO download (ie. check it's checksum). It's covered in the Lubuntu manual page covering "Retrieving the Image" too  (*okay I have a script that has automated this task as I'm doing this many times per week*)

[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)


Next I write the ISO to media (myself I'll use `mkusb`, but the manual page for that step offers many options ([https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html))

Finally is the booting, covered in the next manual section. Refer [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

The option I will choose is "Start Lubuntu", however if your box has graphics issues, the next option is what I'd likely pick (ie. "Start Lubuntu (safe graphics)"). Refer to [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html) for the image.

When the install media check is performed, do **NOT** skip it.  Failed writes occur, as flash media isn't perfect (my problem currently... they have only a limited number of writes available before they given problems!)

---

### Post by devilriderman on 2020-06-06
I mean that I have no problem putting the iso, onto the flash drive and it gives the install options page, "Install Lubuntu, Install Lubuntu image safe(I think), Reboot from hard Drive" etc.  4 options but no "Try Lubuntu without installing" option.

---

### Post by guiverc on 2020-06-06
Where did you get it from?

I'm aware there search engines regularly point people to other (non-Ubuntu/non-Lubuntu) sites when they search for "Lubuntu" (*and if people don't check it, they may download the ISO from a unofficial site thus end up with something that isn't Lubuntu*), but current ISOs should offer what is seen in the manual links I provided earlier (with the minor exception of the "*Check disk for defects*" doesn't appear on 20.04 as it's done automatically; it'll get removed from the manual once 19.10 is EOL as *eoa* users still have that option.

My best guess is you asked a search engine where to grab Lubuntu from, and thus downloaded something that isn't an official image (or maybe just something old at best).  Which site you go to depends on the language you use in search engines, but Lubuntu's site doesn't have advertizing, so seems not to be favored by google which sends searchers to other sites depending on their language of query (is even wrong for english)...

If this is correct, and you're unsure of what site is legitimate/correct, seek direction from ubuntu.com, where you'll end up at [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will send you to the correct web site for whatever Ubuntu flavor you want (and you'll end up at lubuntu.me for Lubuntu).

I would go to [http://cdimage.ubuntu.com/lubuntu/releases/20.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/20.04/release/) and grab a checksum and verify your image is legitimate, my best guess is you didn't download from the legitimate site.

(lubuntu[.]net to my knowledge has never offered bad ISOs if you got it from there, but it's **not** under Ubuntu or Lubuntu control, and it is often out-of-date and giving wrong ISOs as a result...  I can't give advice on the other sites google sends people to if you don't use english, except they aren't under the control of either Lubuntu or Canonical/Ubuntu, and I wouldn't trust them.  *My advice is to not trust google for official sites unless you know how to verify the results*)

---

### Post by devilriderman on 2020-06-06
[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) there

---

### Post by devilriderman on 2020-06-06
Hmm.  Interesting what you say.  Lubuntu.net doesn't seem to have the 20.04 version.  I'd be suprised 20.04 seems to be spoken about a lot on youtube.

---

### Post by guiverc on 2020-06-06
The lubuntu[.]net site is neither a Ubuntu, nor a Lubuntu site. 

The maintainer of it **was** a maintainer of Lubuntu but left the project, but as he created & owned the web site, and didn't want to give that up, it's remained his, and a new `lubuntu.me` web site was created for the project.

Canonical (*the company behind Ubuntu*) of course controls ubuntu.com, so it always points to the correct site, ie. lubuntu.me (what I used in example in the prior message).  If you want to get more detail, maybe you could look up [https://ubuntuforums.org/showthread.php?t=2360662](https://ubuntuforums.org/showthread.php?t=2360662)

Because the .net site never directly served ISOs  (letting users download them from ubuntu.com avoiding bandwidth costs) users got valid files, but on occasion not the file they wanted (if new ISOs came out, the .net site was regularly providing links to an older ISO and or without wanted fixes).

It's not the only site offering to let you download Lubuntu though found on google :(

---

### Post by devilriderman on 2020-06-06
Wow!  Thanks.  So much one can learn about Ubuntu!  How would anyone else even know, if they didn't with someone informed like yourself!  Crazy.  That's good to know.  So, it looks I downloaded the correct version of Lubuntu.  Still no idea why it doesn't offer "Try Lubuntu without...."

Thanks for your help so far.  Appreciate it.

---

### Post by devilriderman on 2020-06-06
Stupid me!  For some reason I didn't take note that it says, "Start Lubuntu"   I was looking too hard for the "Try Lubuntu without installing"  I'm actually typing this from the Lubuntu usb install.  Really impressed.  It looks smart, and is lightning quick.  I'm gonna switch from Linux Mint.  Mint is alright.  I got 4gb, Lenovo Ideapad 110.  It lags a little on Mint.  I think will be faster.  Thanks again for all your help [**[COLOR=#DD4814][B]guiverc**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=2074246") :)

---

### Post by CelticWarrior on 2020-06-07
A [Lenovo Ideapad 110]("https://www.lenovo.com/br/pt/laptops/ideapad/serie-100/IdeaPad-110-15IBR-/p/88IP1000708") is what it is. With its Intel® Celeron&#8482; N3060 and integrated Intel® HD Graphics 400 it isn't a fast and powerful machine by any stretch of imagination.

---

### Post by GhX6GZMB on 2020-06-07
> **CelticWarrior said:**
> A [Lenovo Ideapad 110]("https://www.lenovo.com/br/pt/laptops/ideapad/serie-100/IdeaPad-110-15IBR-/p/88IP1000708") is what it is. With its Intel® Celeron™ N3060 and integrated Intel® HD Graphics 400 it isn't a fast and powerful machine by any stretch of imagination.

A 2 GHz AMD CPU with 4 GB RAM is perfect for Lubuntu. I've no idea where your specs came from?

---

### Post by CelticWarrior on 2020-06-08
> **ml9104 said:**
> A 2 GHz AMD CPU with 4 GB RAM is perfect for Lubuntu. I've no idea where your specs came from?

There's a link in case you want to open its specifications page.

---

### Post by ActionParsnip on 2020-06-08
More grunt than anything I have..... It'll be fine.

---

### Post by GhX6GZMB on 2020-06-08
> **CelticWarrior said:**
> There's a link in case you want to open its specifications page.

A Lenovo Ideapad 110 can be several things, but not the one you found.

---

### Post by CelticWarrior on 2020-06-08
> **ml9104 said:**
> A Lenovo Ideapad 110 can be several things, but not the one you found.

So, according to you, the manufacturer's website has wrong specifications? By all means, please post a link to the correct specifications.

---

### Post by GhX6GZMB on 2020-06-08
> **CelticWarrior said:**
> So, according to you, the manufacturer's website has wrong specifications? By all means, please post a link to the correct specifications.

Well, there's an Ideapad 110-15 (15") with i3. And there's Ideapad 110-17 (17") with i5. And there's an Ideapad 110-17 (17") with i7. And there's an Ideapad 110-17 (17") with AMD A8. And probably more, depending on market.

Extending a local Spanish offering to the world doesn't seems to work. Sorry.

---

### Post by QIII on 2020-06-08
OK.  The OP's problem seems to have been resolved.  There is no reason to get into a marking contest.

Closed.

---

