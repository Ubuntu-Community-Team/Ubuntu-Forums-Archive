---
title: "Evolution Minimize"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2010-04-05
So, I see that the indicator applet has a mail option, and upon setting up Evolution, it doesn't hide like Empathy does.  Whats the sense of having evolution in the applet if you still have to keep it open?

Any way to make it minimize like empathy does?

---

### Post by Rackstar on 2010-04-05
I was thinking the exact same thing today. Same counts for Rhytmbox.

---

### Post by zoomy942 on 2010-04-05
> **Rackstar said:**
> I was thinking the exact same thing today. Same counts for Rhytmbox.

?  my rythombox drops to the tray when i click the X.  yours doesnt?  I just want evolution to do that... hell - same for gwibber since it always says "configure broadcast account" in the tray.

---

### Post by Killigrew on 2010-04-06
hi, as far as i know evolution can not do it,
in the past people use extra programs like AllTray for this
but with them you would have an extra Tray Icon which is
surely not what you want ;)
even Evolution 2.30 doesn't have the feature as i know.
it is sad, looking for the time it is requested, it must be a hell to implement...
or the devs don't care that much about user wishes...
at least things get better with 2.30 for me -> less bugs ;)

greetings

---

### Post by dcstar on 2010-04-06
> **zoomy942 said:**
> So, I see that the indicator applet has a mail option, and upon setting up Evolution, it doesn't hide like Empathy does.  Whats the sense of having evolution in the applet if you still have to keep it open?


AFAIK the applet is to launch **any** default mail client that you have.

---

### Post by zoomy942 on 2010-04-06
> **dcstar said:**
> AFAIK the applet is to launch **any** default mail client that you have.

wait - so i could use thunderbird and it would work in the applet?  does thunderbird minimize to tray?

---

### Post by Killigrew on 2010-04-06
as far as i know it is not possible, you can use a plugin but as in evolution you'll have an extra tray icon. if you find way, please let us know :)

greetings

---

### Post by termilus on 2010-04-06
there is a way to get evolution start minimized in tray with only one icon there.

I've tested and succeed in ubuntu 9.10 karmic amd64

1.) download the source of a plugin called "evolution-tray" from [http://gnome.eu.org/evo/index.php/Evolution_Tray](http://gnome.eu.org/evo/index.php/Evolution_Tray)

(I have taken that: evolution-tray-0.0.3 (courtesy of Edwin Stang) )

2.) unpack the file

3.) change to root directory of the unpacked sources

4.) read the readme-file there: .../INSTALL and follow the instructions

5.) use apt / synaptic or something else to get required packages to succesful configure the sources (you need "dev"-packages - they are not installed usually in ubuntu)

6.) make ... make install ... (see the INSTALL-file)

7.) after success the evolution-tray-plugin is available in evolution after restarting the mail-program - got to preferences --> plugins --> evolution tray and toggle to start evolution minimized only with trayicon next time

I hope that will help in lucid to.

... sorry for my bad english ... greetings from germany ;-)

---

### Post by Killigrew on 2010-04-07
hey, that sound good, to bad i get the folling error message with ./configure:
```

checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for TRAY_EPLUGIN... yes
configure: error: Unable to find image directory

```

greetings

---

### Post by ytecle on 2010-04-07
Hi,
How do I post a new threat?
Thanks!

---

### Post by philinux on 2010-04-07
> **ytecle said:**
> Hi,
How do I post a new threat?
Thanks!

Click the **New Thread** link on the Forum Page.

---

### Post by philinux on 2010-04-07
> **zoomy942 said:**
> So, I see that the indicator applet has a mail option, and upon setting up Evolution, it doesn't hide like Empathy does.  Whats the sense of having evolution in the applet if you still have to keep it open?

Any way to make it minimize like empathy does?

The other option is to use alltray which is in the repos.

---

### Post by termilus on 2010-04-07
> **Killigrew said:**
> hey, that sound good, to bad i get the folling error message with ./configure:
```

checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for TRAY_EPLUGIN... yes
configure: error: Unable to find image directory

```greetings

is that the full errormessage? - please send the full one, if there are some more information available

---

### Post by termilus on 2010-04-07
> **philinux said:**
> The other option is to use alltray which is in the repos.

ys it is. I've tried alltray but I've got a bug - I was not able to drag and drop mails from my incoming folder to other self created ones inside evolution with my mouse. I must use the context menu with " ... move mail to folder ...". 

this bug only appears while using alltray.

(ubuntu 9.10 / evolution 2.28.1 / alltray 0.69)

---

### Post by Killigrew on 2010-04-07
the last line is the complete error message 
i got it fixed like i wrote in my last post
./configure ends now without an error but make does not.
I think the problem is that i'm using evolution 2.30 and not 2.28

greetings

---

### Post by zoomy942 on 2010-04-07
wait - so that plugin will make it do what I first posted about?  Any try it yet?

---

### Post by termilus on 2010-04-07
@killigrew

so if make does not work - perhaps you do need all the necessary files to build any installs from scratch - these are not installed automatically by ubuntu

if you want to give a try - take this:

```
sudo apt-get install build-essential
```

good luck ;-)

@zoomy942

what this plugin does:

* start evolution in minimized mode (only one icon in tray)
* maximize and minimize evolution by clicking on the icon

what this plugin doesn't do

* it does not run outside evolution - you always have to start evolution to get informed about new Mail 
* it doesn't inform you about nee mails

(if you search for this functionality - please take a look at screenlets used with compiz - I think there is what you want: "mailcheck")

---

