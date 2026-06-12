---
title: "Update Manager Error in VirtualBox"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by Jubst on 2012-04-14
Hello, I was trying to check updates in the Update Manager on Ubuntu in my Virtual Machine, but the following error came up:

E: type '"deb" is not known on line 57 in source list /etc/apt/sources.list'

I also notice that my Software Center, when clicked, will not respond. The only thing I did do was try to install Torchat through the terminal... :(

Can anyone help me??? Or do I have to reinstall Ubuntu...

---

### Post by Elfy on 2012-04-14
Not sure what you did to cause it but the source list should only have lines starting with deb, deb-src or # anything else will cause an error

Open a terminal then run this to backup the file

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
```

Once that is done open the file for editing - to do this you need root priveleges

```
gksudo gedit /etc/apt/sources.list
```

Check the line - it looks like it will be 

"deb" 

Change that to be 

deb

Save and exit, now run this in a terminal and check for errors

```
sudo apt-get update
```

If you are lost and would like more specific help, run this from a terminal and paste the _whole_ output here for us

```
cat /etc/apt/sources.list
```

---

