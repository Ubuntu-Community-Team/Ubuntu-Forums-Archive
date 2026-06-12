---
title: "How safe is the this Alpha release regarding hardware?"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-12-10
Should i go ahead and use this alpha image on my laptop. I am concerned about its effect on my hardware. This is not really a productive laptop and i use it for fun stuff but i do use it.

Regards,
SK.

---

### Post by VMC on 2009-12-10
That would be entirely up to you. You can boot up the LiveCD and test it for a while to see if everything works and then install it. 

Unless you were going to wipe your hard drive, Ubiquity should install alpha without issues.

---

### Post by kevpan815 on 2009-12-10
It's Running Just Fine On My Dell XPS 630I, Just Stay Away From The Integrated NVIDIA 185 Series Device Driver, Found That Out The Hard Way!

---

### Post by donniezazen on 2009-12-10
> **kevpan815 said:**
> It's Running Just Fine On My Dell XPS 630I, Just Stay Away From The Integrated NVIDIA 185 Series Device Driver, Found That Out The Hard Way!

Have you tried Nvidia 173 series driver?

Thanks

---

### Post by kevpan815 on 2009-12-10
> **soham_1207 said:**
> Have you tried Nvidia 173 series driver?

Thanks

No I Have Not Tried The NVIDIA 173 Device Driver, And I Am NOT Going 2 try it either, as there is something mentioned in the Known Issues about NVIDIA Device Drivers Not Working In Alpha 1, I Simply Did NOT Read The Release Notes Before I Started Messing Around With Alpha 1, Because I Started Downloading It After The Archive Update In Progress Message Went Away, However Before The Official Announcement Came Out, Just FYI!

---

### Post by Jordanwb on 2009-12-11
> **kevpan815 said:**
> as there is something mentioned in the Known Issues about NVIDIA Device Drivers Not Working In Alpha 1

That's good to know. I have a nvidia card and was going to install, but I guess I'll pass.

---

### Post by SuperSonic4 on 2009-12-11
> **soham_1207 said:**
> Should i go ahead and use this alpha image on my laptop. I am concerned about its effect on my hardware. This is not really a productive laptop and i use it for fun stuff but i do use it.

Regards,
SK.

Nobody knows :popcorn: thats what the alpha is for - to test.

> **kevpan815 said:**
> No I Have Not Tried The NVIDIA 173 Device Driver, And I Am NOT Going 2 try it either, as there is something mentioned in the Known Issues about NVIDIA Device Drivers Not Working In Alpha 1, I Simply Did NOT Read The Release Notes Before I Started Messing Around With Alpha 1, Because I Started Downloading It After The Archive Update In Progress Message Went Away, However Before The Official Announcement Came Out, Just FYI!

Doesn't It Get Very Annoying Typing Every Word In Caps. Your Poor Shift Key :(

---

### Post by phenest on 2009-12-11
> **soham_1207 said:**
> Should i go ahead and use this alpha image on my laptop. I am concerned about its effect on my hardware. This is not really a productive laptop and i use it for fun stuff but i do use it.

Regards,
SK.

Are you concerned about physical damage or just whether it will work?

---

### Post by pedja_portugalac on 2009-12-11
I'll test it within an hour. Also I'll install nvidia-vdpau 190.42 from ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic) and let you know then. Everybody, who have little bit more knowledge about Ubuntu, should test because it's only like that we can have our final system faster.

---

### Post by donniezazen on 2009-12-11
> **pedja_portugalac said:**
> I'll test it within an hour. Also I'll install nvidia-vdpau 190.42 from ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic) and let you know then. Everybody, who have little bit more knowledge about Ubuntu, should test because it's only like that we can have our final system faster.

Is this for all Nvidia graphic cards or latest series? Can i try it on my Dell Inspiron 6400/E1505 wit Nvidia GeForce 7300?

Thanks

---

### Post by donniezazen on 2009-12-11
> **phenest said:**
> Are you concerned about physical damage or just whether it will work?

Exactly I was not asking about hardware support but hardware/physical damage. On the other hand Ubiquity is crashing while manual partitioning, so , i really cant try it for few more days until i get my external hard drive to even backup useless data.

Thanks.

---

### Post by kevpan815 on 2009-12-11
Update: It Works Just Fine With The Latest Beta NVIDIA Device Driver From [http://www.nvidia.com](http://www.nvidia.com), Just FYI!

---

### Post by pedja_portugalac on 2009-12-11
> **soham_1207 said:**
> Is this for all Nvidia graphic cards or latest series? Can i try it on my Dell Inspiron 6400/E1505 wit Nvidia GeForce 7300?

Thanks

They are talking about outdated 180 nvidia driver which is in official ubuntu repository and now on alfa CD. I am talking about latest, but unofficial, 190.42 nvidia-vdpau driver from ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic)
Vdpau is helping your processor while watching High Definition videos, I don't know if "you" need that, I need, but in any case latest driver with or without vdpau is recommended by myself.

> **kevpan815 said:**
> Update: It Works Just Fine With The Latest Beta NVIDIA Device Driver From [http://www.nvidia.com](http://www.nvidia.com), Just FYI!
Good to know.

---

### Post by donniezazen on 2009-12-11
> **kevpan815 said:**
> update: It works just fine with the latest beta nvidia device driver from [http://www.nvidia.com](http://www.nvidia.com), just fyi!

+1

---

### Post by Gina on 2009-12-11
Just tried to download that driver but instead of downloading, Firefox insists on displaying it!  And I thought we might be getting somewhere!

---

### Post by phenest on 2009-12-12
> **soham_1207 said:**
> Exactly I was not asking about hardware support but hardware/physical damage. On the other hand Ubiquity is crashing while manual partitioning, so , i really cant try it for few more days until i get my external hard drive to even backup useless data.

Thanks.

nVidia tend to give better support for their cards than other manufacturers, and I would guess it's a more popular brand too. As such, the drivers are extensively tested by nVidia and users and I've not heard of anyone getting physical damage to their video cards. If you have any concerns, you could always register on [nvnews]("http://www.nvnews.net/"). They have a Linux section.

---

### Post by donniezazen on 2009-12-12
> **pedja_portugalac said:**
> They are talking about outdated 180 nvidia driver which is in official ubuntu repository and now on alfa CD. I am talking about latest, but unofficial, 190.42 nvidia-vdpau driver from ppa [https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=karmic)
Vdpau is helping your processor while watching High Definition videos, I don't know if "you" need that, I need, but in any case latest driver with or without vdpau is recommended by myself.


Good to know.

Confirmed Nvidia 190.42 installed from ppa killed my display.

---

