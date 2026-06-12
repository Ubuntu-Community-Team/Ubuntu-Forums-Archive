---
title: "[SOLVED] ubuntu themes"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by brunoskrebs on 2007-08-30
Hi, I`ve installed an ubuntu theme in my system. And I wnat to know if it could be dangerous for the security of my system. Because I executed a few commands that the page told me to do in order to put this theme in my computer...

The theme that I had download is from this site: [http://ubuntusatanic.org/installation.php](http://ubuntusatanic.org/installation.php)

Do think that they are trustful?

Thank you,
Bruno Krebs

---

### Post by callan79 on 2007-08-30
> **brunoskrebs said:**
> Hi, I`ve installed an ubuntu theme in my system. And I wnat to know if it could be dangerous for the security of my system. Because I executed a few commands that the page told me to do in order to put this theme in my computer...

Hey Bruno,

Well, when you apt-get something, you're basically downloading a zip of some files, which has a script inbuilt that tells your system where to put those files, and what to do.

So if someone made something nasty, then potentially yes there could be a problem, so you really would not want to be installing stuff from potentially dodgy sources.

I guess really you need to decide if you trust the site you're downloading from - just like in Windows, you make sure you download your setup.exe from a trusted site, not some dodgy site.

By the way - I have Ubuntu Satanic installed too, it's pretty cool :)

Cheers
Callan

---

### Post by wolfen69 on 2007-08-30
as far as i know, they are trustworthy. i love their wallpapers.

---

### Post by brunoskrebs on 2007-08-30
hehheheh

Yeah it is a good theme indeed. So you trusted the site too. Anybody else installed this, or can tell me if they are trustfull or not?

Thank you.
Bye

---

### Post by parker13 on 2007-08-30
Hi Guys,

The commands you ran to download the GPG key are actually intended to verify the authenticity of the packages and protect you from any malicious content. However, I can understand your concern at typing a load of cryptic writings into your terminal.

I'd like to assure you that there is nothing evil Ubuntu SE - apart from the themes themselves of course. ;-) 

To put your minds at rest, you can see exactly what each package installs by running, for example:

```
dpkg -L satanic-wallpapers
```

You won't see anything that can do any harm to your system.

Glad you like the themes, by the way!
Garry.

---

### Post by gundumfx on 2007-08-30
> **wolfen69 said:**
> as far as i know, they are trustworthy. i love their wallpapers.

well i love there wall papers but i want to change my login screen well can you help me do that

---

### Post by parker13 on 2007-08-30
> **gundumfx said:**
> well i love there wall papers but i want to change my login screen well can you help me do that

Hi Gundumfx,

You should be able to change both the login screen and bootup (usplash) screen by following the instructions on:

[http://ubuntusatanic.org/installation.php](http://ubuntusatanic.org/installation.php)

and then

[http://ubuntusatanic.org/configuration.php](http://ubuntusatanic.org/configuration.php)

It's pretty straightforward. If you get stuck at any point, then post any questions here and I'll try to help.

---

### Post by parker13 on 2007-08-30
May I also point out that if people are still concerned about the authenticity of SE, the code is all checked in under Bazaar source control on Lauchpad for you to browse:

[https://launchpad.net/satanic](https://launchpad.net/satanic)

In fact, I intend to move the packages to be built and served from Launchpad once the new Personal Package Archive tools are available, which should be very soon.

---

### Post by brunoskrebs on 2007-08-30
hey thanks for the answers

by the way I hope u didnt get angry with my question you know...

I was not intend to doubt on anybody, it is just that I`m really newbie to linux, and I don`t know the meaning of a lot of commands that I`m typing hehehehhe

but thanks again, and keep the good work...

cheers

ps. if you want hear from a "customer" of your theme, I think that would be great if it changed the colors and buttons of the windows and panels too. I know that it is probably a very hard work. but I don`t know if you work alone or what, and it is just an idea...

---

### Post by parker13 on 2007-08-31
> **brunoskrebs said:**
> hey thanks for the answers

by the way I hope u didnt get angry with my question you know...

I was not intend to doubt on anybody, it is just that I`m really newbie to linux, and I don`t know the meaning of a lot of commands that I`m typing hehehehhe

but thanks again, and keep the good work...

cheers

ps. if you want hear from a "customer" of your theme, I think that would be great if it changed the colors and buttons of the windows and panels too. I know that it is probably a very hard work. but I don`t know if you work alone or what, and it is just an idea...

Hey, I'm not angry at all. It's really good that you aired your concerns here and I may even put a page on the site detailing some of what's been discussed here and hopefully put other people's minds at rest.

There are some window and icon themes on the download page:

[http://ubuntusatanic.org/download.php](http://ubuntusatanic.org/download.php)

They're not by me, but have a nice dark feel which you might like. I'd like to produce much more bespoke icons and themes for SE, but I've been spending too much time on the Eternity Screensaver project recently. Maybe in the future...

---

