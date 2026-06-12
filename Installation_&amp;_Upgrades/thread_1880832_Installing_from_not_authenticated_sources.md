---
title: "Installing from not authenticated sources"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2011-11-14
Hello,

Some days ago I tried to install Firefox, but got stuck at the 'requires installation of untrusted packages' error, until members of this forum [hinted]("http://ubuntuforums.org/showthread.php?p=11446322#post11446322") how to bypass the Software Center installation via terminal.

That was all fine, but I get the same error w/ other applications. Minutes ago I tried installing the indicator-sysmonitor 0.3.9 app via the .deb file (like the initial Firefox installation I tried) and got to the same message: [https://lh3.googleusercontent.com/-Uxlyqa3C8Po/TsE779yi8pI/AAAAAAAADHU/-l312n2KkSE/s0/Screenshot%252520at%2525202011-11-14%25252020%25253A02%25253A10.png](https://lh3.googleusercontent.com/-Uxlyqa3C8Po/TsE779yi8pI/AAAAAAAADHU/-l312n2KkSE/s0/Screenshot%252520at%2525202011-11-14%25252020%25253A02%25253A10.png)

So now I would like to know if there is a way to edit software source settings so that I can enable such installations w/o this error message, or at least some method to fix it for each time I install something.

Thanks in advance.

---

### Post by Tornikee on 2011-11-14
Nothing? (

---

### Post by Lars Noodén on 2011-11-14
When I've had this error, it's been because the package index files on the computer are out of date.  I'm not sure how to force an update in the Software Center, but in the shell it is this:

```

sudo apt-get update

```

---

### Post by Tornikee on 2011-11-14
Yep that's what was advised in the Firefox case, followed by

```
sudo apt-get install Firefox
```

But changing Firefox to the desired app name doesn't always work, namely in this case of indicator-sysmonitor app.

---

### Post by Lars Noodén on 2011-11-14
I don't see any package with that name in the repository.  What is it called in the repository?

---

### Post by Tornikee on 2011-11-14
I only see the name my screenshot in the first post shows. And [this]("http://www.omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29") is where I got the .deb file from, same name for the app.

---

### Post by Tornikee on 2011-11-17
The Software Center now displays the mentioned error even for regular updates like:
[https://lh4.googleusercontent.com/-K00a6ikQHJY/TsVcWCzm36I/AAAAAAAADI4/ipysvuhvsak/s0/Screenshot%252520at%2525202011-11-17%25252023%25253A10%25253A44.png](https://lh4.googleusercontent.com/-K00a6ikQHJY/TsVcWCzm36I/AAAAAAAADI4/ipysvuhvsak/s0/Screenshot%252520at%2525202011-11-17%25252023%25253A10%25253A44.png)

Also, how can I prevent notifications like this:
[https://lh6.googleusercontent.com/-_VeJ6X-jrqs/TsVdsXDL3DI/AAAAAAAADJM/PkCoF11yW98/s0/Screenshot%252520at%2525202011-11-17%25252023%25253A16%25253A10.png](https://lh6.googleusercontent.com/-_VeJ6X-jrqs/TsVdsXDL3DI/AAAAAAAADJM/PkCoF11yW98/s0/Screenshot%252520at%2525202011-11-17%25252023%25253A16%25253A10.png)

---

