---
title: "So annoying bugs!"
date: 2012-03-30
forum: Installation &amp; Upgrades
---

### Post by Thebuntuway on 2012-03-30
Well, these is an awkward!..I had tried to install Google Chrome in my Kubuntu, and these is what happen next. It tell there are many bugs and the muon package installer keep crasing and sometimes, when a 'dumb bugs' appears, the screen will turn black for about a few second. It will come back to the normal windows later on but the 'origin' kubuntu effect (fade out, fade in, scrool option style, the blueish ligh behind windows) are gone away and it seems like im using a very  old 'caveman' personal computer after that. So annoying! I have been reinstall these OS for many many time because of these stupid bugs and other dumb crap happen in these os!...even i watching you tube, it turn jammed suddenly and will jammed forever and make me just pull of the power plug and there you solved the jammed probs. IT KEEPS HAPPEN IN A TIME...EVEN A WEEK I HAVE ESTIMATE THAT I REINSTALL THESE OS FOR MORE THAN 7 OR 8 TIMES!!..I FREAKIN HATES THIS!!!..These problem had less that ubuntu before, only my stupid netbook strenght just cannot handle it awesomeness. Any BUNTUGENIUS HERE, please help me fellas!..before i buy windows xp service pack 3...help?:confused:

---

### Post by SeijiSensei on 2012-03-30
I just tried installing the open-source version of Chrome on Kubuntu 12.04 beta with:

```
sudo apt-get install chromium-browser
```

Does that work for you?

---

### Post by mörgæs on 2012-03-30
Please give a complete hardware description.

---

### Post by Thebuntuway on 2012-03-30
> **SeijiSensei said:**
> I just tried installing the open-source version of Chrome on Kubuntu 12.04 beta with:

```
sudo apt-get install chromium-browser
```

Does that work for you?

Doesn't work well dude...still crash and appear the bugs windows..

---

### Post by Thebuntuway on 2012-03-30
> **mörgæs said:**
> Please give a complete hardware description.

Here you are!
Acer Aspire One D255
Ram:1GB
Processor:Intel Atom Prosessor N550 (1GHz, 1MB L2 cache)
Graphic card:GMA 3500

So then??

---

### Post by lisati on 2012-03-30
> **Thebuntuway said:**
> Doesn't work well dude...still crash and appear the bugs windows..

Have you filed a bug report? Or do you mean "errors" when you talk of "bugs"?

---

### Post by Thebuntuway on 2012-03-31
> **lisati said:**
> Have you filed a bug report? Or do you mean "errors" when you talk of "bugs"?

IDK...i think both of it..because it said error and bugs..IDK...

---

### Post by mörgæs on 2012-03-31
> **Thebuntuway said:**
> Here you are!
Acer Aspire One D255
Ram:1GB
Processor:Intel Atom Prosessor N550 (1GHz, 1MB L2 cache)
Graphic card:GMA 3500

So then??

Then I would try something lighter than Ubuntu. Have you tried a fresh install of Xubuntu or Lubuntu?

---

### Post by Zorael on 2012-03-31
> **Thebuntuway said:**
> Well, these is an awkward!..I had tried to install Google Chrome in my Kubuntu, and these is what happen next. It tell there are many bugs and the muon package installer keep crasing
Sadly, although Muon is in rapid development it's still young and a bit rough around the edges. Have you tried a different package manager? There are a few notable graphical ones like [**the Ubuntu Software Center**](apt://software-center) and [**Synaptic**](apt://synaptic) -- and then there's the terminal **apt-get** and [**aptitude**](apt://aptitude). If you're trying to install the official Chrome .deb file instead of the open-source [Chromium](apt://chromium-browser) that's available from the repositories, you'll need to use **dpkg** or [**gdebi**](apt://gdebi-kde) directly instead. Google around and you should find some informative guides.

You may also want to consider adding the [**Kubuntu PPA**](https://launchpad.net/~kubuntu-ppa) sources for updates to the majority of KDE and Kubuntu packages. There is a guide for this over on [this wiki page](https://help.ubuntu.com/community/Repositories/Kubuntu).

> **Thebuntuway said:**
> [...] and sometimes, when a 'dumb bugs' appears, the screen will turn black for about a few second. It will come back to the normal windows later on but the 'origin' kubuntu effect (fade out, fade in, scrool option style, the blueish ligh behind windows) are gone away and it seems like im using a very  old 'caveman' personal computer after that. So annoying! I have been reinstall these OS for many many time because of these stupid bugs and other dumb crap happen in these os!...even i watching you tube, it turn jammed suddenly and will jammed forever and make me just pull of the power plug and there you solved the jammed probs.
This happens when the window manager (**KWin**) notices that something goes wrong with your videocard and/or their drivers, and thus suspends [*compositing*](http://en.wikipedia.org/wiki/Compositing_window_manager) (desktop effects) to try to avoid a complete crash.
> **Wikipedia]A compositing window manager is a type of window manager (software that draws a graphical user interface on a computer display), that unlike earlier window managers which made each individual program responsible for rendering its own window directly inside the display memory, provides applications an off-screen buffer for window memory and composites windows into an image representing the screen and writes the result into the display memory.

Compositing window managers may perform additional processing on buffered windows, applying 2D and 3D animated effects such as blending, fading, scaling, rotation, duplication, bending and contortion, shuffling, blurring, redirecting applications, and translating windows into one of a number of displays and virtual desktops. Computer graphics technology allows for visual effects to be rendered in real time such as drop shadows, live previews, and complex animation. Since, technically, the screen is double buffered, it does not flicker during updates.[/quote]
If everything turns black and nothing seems to work, that indicates a GPU hang. It's difficult to know *why* this happens, but I'd wager it's due to buggy drivers. It may even be possible to track it down to a single KWin effect plugin (that's provoking this driver bug), but that's not really easy work. You could try keeping effects enabled but disabling most plugins, especially Blur.

Have you tried enabling all the update repositories?

[img]https://help.ubuntu.com/community/Repositories/Kubuntu/Intrepid?action=AttachFile&do=get&target=snapshot21.png[/img]

If all else fails, you could add the [**xorg-edgers**](https://launchpad.net/~xorg-edgers) PPA repository for *very* fresh drivers. They aren't officially supported, but in my experience they work well enough or even better than the repository ones. The wiki page I linked earlier details how to add PPAs -- though you could do it in a terminal with a single command, naturally. :>

```
$ sudo add-apt-repository **ppa:xorg-edgers/ppa**       *# updates to X.org and its drivers, may help "black screen" crashes*
$ sudo add-apt-repository **ppa:kubuntu-ppa/ppa**       *# minor updates and bug fixes to Kubuntu and KDE (eg 4.7.**_3_** -> 4.7.**_4_**), may help Muon crashes but won't introduce new features *
$ sudo add-apt-repository **ppa:kubuntu-ppa/backports** *# newer point-release versions of KDE (eg 4.**_7_**.4 -> 4.**_8_**.0)[ backported to 11.10 ](https://wiki.ubuntu.com/UbuntuBackports)*
```
Then either upgrade your packages via Muon or via a terminal.
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install **chromium-browser**             *# :>*
                                                    *# reboot to let everything sink in, and hope for the best*
```
[QUOTE=Thebuntuway said:**
> IT KEEPS HAPPEN IN A TIME...EVEN A WEEK I HAVE ESTIMATE THAT I REINSTALL THESE OS FOR MORE THAN 7 OR 8 TIMES!!..I FREAKIN HATES THIS!!!..These problem had less that ubuntu before, only my stupid netbook strenght just cannot handle it awesomeness. Any BUNTUGENIUS HERE, please help me fellas!..before i buy windows xp service pack 3...help?:confused:
Linux allows for a *LOT* of troubleshooting and debugging; it's just difficult to help by forum post instead of actually sitting at your computer. :<

So if you have a linuxy friend, bribe him with something tasty so he'll come help.


Lastly, never force a power off! Please see this wiki page on [Raising Elephants](http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot). It may be difficult to manage the key combination on a laptop, but this works on mine;
[list=1][*]Press and hold Alt
[*]Press and hold Fn
[*]Press and hold Print Screen/SysRq
[*]Release Fn (but keep holding Alt and Print Screen/SysRq)
[*]Press **R E I S U B** (not too fast, in particular let your hard drive stop spinning after **S** before continuing.)[/list]

---

