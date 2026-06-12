---
title: "Beryl Problem"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by AirAshby on 2007-01-21
I was following this [HowToGuide]("https://help.ubuntu.com/community/BerylOnEdgy#head-a11bb15fcef71ada47e68894e33894659c648026") but when i get to this stage;
```
sudo apt-get install beryl emerald-themes
```
I get the following response;
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: beryl-manager but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages

```
Can anyone help cause I really want this to impress my friends and clients into getting Ubuntu and stop them upgrading to Vista.

---

### Post by JamieC on 2007-01-21
Try the following commands:
```

sudo apt-get update
sudo aptitude install beryl emerald-themes

```

---

