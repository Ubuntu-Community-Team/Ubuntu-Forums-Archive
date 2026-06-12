---
title: "Cannot complete Voxelands installation"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by dommel2002 on 2017-07-24
I was installing Voxelands with [B]wget [http://www.voxelands.com/downloads/voxelands-1507.00-ubuntu-x86_64.deb](http://www.voxelands.com/downloads/voxelands-1507.00-ubuntu-x86_64.deb) &
sudo apt-get install gdebi & sudo gdebi voxelands-1507.00-ubuntu-x86_64.deb
[/B]when I got this output: 
[I]Reading package lists... Done
Building dependency tree        
Reading state information... Done
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
[/I]
Can anyone help me?

---

### Post by vocx on 2017-07-24
> **dommel2002 said:**
> I was installing Voxelands with [B]wget [http://www.voxelands.com/downloads/voxelands-1507.00-ubuntu-x86_64.deb](http://www.voxelands.com/downloads/voxelands-1507.00-ubuntu-x86_64.deb) &
sudo apt-get install gdebi & sudo gdebi voxelands-1507.00-ubuntu-x86_64.deb
[/B]when I got this output: 
[I]Reading package lists... Done
Building dependency tree        
Reading state information... Done
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
[/I]
Can anyone help me?
I don't use "gdebi" to install packages.

If you downloaded the deb package, you can install it with "dpkg".
```

sudo dpkg -i voxelands-1507.00-ubuntu-x86_64.deb

```

Please use "```
" tags when you post terminal output in this forum. There is an opening tag and a closing tag.
[PHP]
[CODE]
some terminal output here

```
[/PHP]

---

