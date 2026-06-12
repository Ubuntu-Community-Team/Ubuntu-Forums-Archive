---
title: "Java problems? Changing from OpenJDK to SunJDK in Maverick"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by redaxe90 on 2011-12-16
If any of you have problems with Java in Maverick and desire switching from the built in OpenJDK to SunJDK, I found an excellent guide.

The guide was meant to help people install a Free PDF reader, but amongst the directions was an excellent guide on how to switch from OpenJDK to SunJDK (sorry for repeating myself, but this is my first ever helpful post on Linux:))

Head over to [Gnostice]("http://www.gnostice.com/nl_article.asp?id=182&t=How_To_Install_Free_PDF_Reader_In_Linux#install_sun_java_runtime_jre_ubuntu_linux").

To be honest, he used the guide to help people making the change using Lucid, but I found that it works perfectly with Maverick as well. If you're running a later model of the OS, then you can maybe run this in a virtual machine, seeing if it works also for 11.04 or even 11.10, perhaps even later models once they're released.

Any sort of feedback would be excellent :)

---

### Post by zvacet on 2011-12-17
If you have two Java versions installed OpenJDK and SunJDK then after installing SunJDK you should run 

```
sudo update-alternatives --config java
```

and select witch one you want to use.

---

### Post by redaxe90 on 2011-12-17
> **zvacet said:**
> If you have two Java versions installed OpenJDK and SunJDK then after installing SunJDK you should run 

```
sudo update-alternatives --config java
```

and select witch one you want to use.

Oddly enough, when I tried to run that command, I got this:

[COLOR="Red"]**update-alternatives: error: no alternatives for java.**[/COLOR]

Which leads me to believe that the method shown on the Gnostice website pushes OpenJDK out of the way completely, though I can't be sure about that. It's the feeling I get, but being a relative newbie I could have been misled :)

---

### Post by redaxe90 on 2011-12-19
I'd like to hear from people running any Ubuntu version, from 10.04 to the latest, to see if anybody could perform this change of JDK packages and if they had to use the ```
sudo update-alternatives --config java
``` command. I got an error message, anybody else?

---

### Post by zvacet on 2011-12-21
Maybe that way remove OpenJDK when installing  SunJDK or you didn´t have and JAva package installed before.I can not think of anything else.

---

### Post by redaxe90 on 2011-12-24
I did a clean install of 10.04 when I set up Ubuntu, then promptly upgraded it to 10.10 (probably near the maximum of what my hardware can run until I set up lubuntu). From what I understand, OpenJDK comes bundled with Ubuntu 10 and later, maybe even earlier versions too (I admit total ignorance about that).

In any case, I never had to configure the java settings or default program, it just changed on it's own during setup.

---

