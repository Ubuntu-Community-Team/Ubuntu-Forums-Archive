---
title: "Error on 13.04 installation?"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by PunchALunch on 2013-06-17
Toshiba Satellite C855

So I tried totally wiping my hard drive and installing 13.04 over my 12.04 LTS, everything went fairly smoothly until soon after I clicked the final installation button.

I get the error "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."

So, what do?

---

### Post by PunchALunch on 2013-06-17
*sigh* Bump

---

### Post by matt_symes on 2013-06-17
Hi

Have you checked the md5sum of the iso ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I would start by verfying that the iso and packages are not corrupted.

Kind regards

---

### Post by PunchALunch on 2013-06-17
Toshiba Satellite C855 - Ubuntu 13.04 w/ Pendrive Linux

> Be me
>Try to erase current partition and install 13.04 over it.
> Get through the installation, encrypt everything,
>Pop-up says "Installer has encountered an unrecoverable error. Now launching desktop environment.:
> No idea what to do.
>Looks at sidebar, notices 3 new drives
>casper-rw, 255 MB Volume, 500 GB Volume (encrypted)
>Open the last one,
>All the files I need are there.
>Win.
>Reboot without installer.
>Black screen with a white cursor in the top left corner for forever.

GUYS WHY.

---

### Post by PunchALunch on 2013-06-17
I tried doing that, but this is on the desktop environment launched by the installer.

The previous OS I had is totally wiped, so (of course,) all of my files, downloads, etc. went with it.

---

### Post by Cheesemill on 2013-06-17
Threads merged.

Please do not start mutiple threads for the same question, it dilutes the community's ability to help.

---

### Post by PunchALunch on 2013-06-17
> **Cheesemill said:**
> Threads merged.

Please do not start mutiple threads for the same question, it dilutes the community's ability to help.


muh bad. Thanks :)

---

### Post by matt_symes on 2013-06-17
Hi

> **PunchALunch said:**
> I tried doing that, but this is on the desktop environment launched by the installer.

The previous OS I had is totally wiped, so (of course,) all of my files, downloads, etc. went with it.

You want to verify that the iso is not corrupted. Can you do this from another machine ?

Anyway, there used to be a bug with the slideshow and some hardware that caused this issue. I thought it was fixed but, as regressions happen, let's rule this out as the problem affecting you.

Boot into the liveCD/USB but befor you hit "install " open a terminal and type

```
sudo apt-get purge ubiquity-slideshow-ubuntu
```

Now hit the install option to try and install ubuntu.

Does this install it ?

Kind regards

---

### Post by PunchALunch on 2013-06-17
Hit an error halfway through installation. I'm on the "Choose a Security Key" screen, Checked off "Overwrite empty disk space" 

and an error pops up.

"An error occured while configuring encrypted volumes, The configuration has been aborted."

---

### Post by matt_symes on 2013-06-17
Hi

As a test, can you install without encryption ?

Encryption is not something i use, however it may be possible to add it later.

Either way, it will implicate/eliminate that as the root cause of the problem.

Kind regards

---

### Post by PunchALunch on 2013-06-17
That worked :) Thanks!

---

### Post by matt_symes on 2013-06-17
Hi

> **PunchALunch said:**
> That worked :) Thanks!

Excellent :)

You may find this link useful.

[http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/](http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)

I don't think much has changed between 12.04 and 13.04, as far as encryption goes, but you may want to double check.

Kind regards

---

