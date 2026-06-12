---
title: "upgrade?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jeremygjohn on 2008-04-27
How do i upgrade from ubuntu 7.10 to 8.04 through like shell since  i cannot reach desktop because of no resume image? or can i get a package to fix that bug??

---

### Post by Pumalite on 2008-04-27
I'd do a clean install after saving data and /home.

---

### Post by jeremygjohn on 2008-04-27
ive tryed that...

---

### Post by Pumalite on 2008-04-27
So, what happened?

---

### Post by jeremygjohn on 2008-04-27
I did reinstall and it still gives no resume image...
im lost on how to fix it?
does the update and upgrade commands make 7.10 go to 8.04? cause  i did sudo apt-get update
    sudo apt-get upgrade 
which has not finished yet

---

### Post by Pumalite on 2008-04-27
Post your specs.

---

### Post by jeremygjohn on 2008-04-27
like as in what hardware?
My video card is NVIDIA Gefore 8600 GT
Dell dimension 5100
2gb ram

---

### Post by steve8track on 2008-04-27
Are you saying x won't start?  Try:

```
sudo dpkg-reconfigure xserver-xorg
```

That should get your desktop back, although with poor performance.  I have the Nvidia 8600M GT, and I had nvidia-glx-new installed.  Just go to restricted drivers and check the box to enable them and it will download and install for you.  System->Administration->Hardware Drivers is where you find the checkbox.  Then it will have you restart.  Alternatively you could install Nvidia's beta drivers by downloading the drivers, installing your kernel headers, uninstalling restricted modules and nvidia-glx-new, and then running the nvidia driver file after disabling gdm through something like:

```
sudo /..pathToGDM/gdm stop
```

and after installing

```
sudo /..pathToGDM/gdm start
```

Use "restart" as a way to quckly stop and start gdm.

I hope I understood what you are trying to do correctly.  It looks like you already upgraded through the command line through:

```
sudo apt-get update
sudo apt-get upgrade
```

or something like that.

Good luck,

Steve

---

### Post by Pumalite on 2008-04-27
To stop your xserver:
sudo /etc/init.d/gdm stop
To start it:
sudo /etc/init.d/gdm start

---

### Post by jeremygjohn on 2008-04-27
i used sudo dpkg-reconfigure xserver-xorg but it says it is not installed?
and upgrade finished using sudo apt-get upgrade but it did nothing still 7.10

---

### Post by jeremygjohn on 2008-04-27
none of those commands work

---

### Post by jeremygjohn on 2008-04-27
ok i did sudo apt-get install xserver-xorg it gets lots of fatal erors and doesnt install correctly i try to do 
sudo dpkg-reconfigure xserver-xorg xserver is broken or not fully installed...
i do startx it returns in the end fatal server error no screens found...

---

### Post by jeremygjohn on 2008-04-27
I did start x finally and i get a green screen with black terminal in the left hand corner and i do sudo-reconfigure xserver-xorg
but what do i do after that?

---

