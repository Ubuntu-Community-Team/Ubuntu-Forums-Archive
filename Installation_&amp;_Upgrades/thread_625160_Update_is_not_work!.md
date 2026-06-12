---
title: "Update is not work!"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by buddingh4x0r on 2007-11-27
I'm running Gutsy atm, and my system seems unable to update itself. I go to System-Adminisration-Update Manager and there's no updates there, and then I click check and input password. It says "Downloading files" and downloads 30 or so files, but then throws up an error message

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I try sudo apt-get update in the terminal and it says the same thing.
Any suggestions?

---

### Post by buddingh4x0r on 2007-11-27
Oh yeah and the same thing happens in Synaptic too

---

### Post by Seisen on 2007-11-27
You need to run this command in the terminal and the update and everything should be fine. This will download the GPG key for the wine repository.

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by buddingh4x0r on 2007-11-27
...it didn't work.
I rank the script and it returned OK 
then I ran update manager and exactly the same thing happened.

---

### Post by buddingh4x0r on 2007-11-28
Bump!
I really need help with this... updates are good things, and to lack them would be catastrophic.

---

### Post by zvacet on 2007-11-29
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
 gpg --export --armor 58403026387EE263  | sudo apt-key add -

---

### Post by PmDematagoda on 2007-11-29
You can also disable the repository if you do not really need it.

1) Open up the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

2) Disable the Wine repository by typing # in front of it, save the file.

3) Run:-

```
sudo apt-get update 
```

And then try updating the system again.

---

