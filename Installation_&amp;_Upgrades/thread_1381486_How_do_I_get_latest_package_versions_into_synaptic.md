---
title: "How do I get latest package versions into synaptic?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Apocc-Rooster on 2010-01-14
I'm trying to install Eclipse from synaptic but it only has version 3.2 while there's a version 3.5 out there. 
How do I get synaptic to provide the latest versions of anything?

Thanks.

---

### Post by Enigmapond on 2010-01-14
Add the Eclipse or any other repository to your sources list. You can get all the info from launchpad...I believe.

---

### Post by Apocc-Rooster on 2010-01-14
Sorry, I know very little about Ubuntu. How do I add it to my sources list and what's launchpad?

---

### Post by steveneddy on 2010-01-14
Install it using the ppa:

[https://launchpad.net/~yogarine/+archive/eclipse](https://launchpad.net/~yogarine/+archive/eclipse)

make sure that you choose the version of Ubuntu that you are using.

What version of Ubuntu are you using?

---

### Post by Enigmapond on 2010-01-14
right...do the above and then follow this tutorial,,,
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by steveneddy on 2010-01-14
I'm gonna have to do this anyway:

Open a terminal

Applications --> Accessories --> Terminal

copy and paste this into your terminal:

```
sudo gedit /etc/apt/sources.list
```

at the bottom of that file add these lines of code: (copy and paste)

```
deb http://ppa.launchpad.net/yogarine/eclipse/ubuntu **[COLOR="Red"]YOUR_UBUNTU_VERSION_HERE[/COLOR]** main 
deb-src http://ppa.launchpad.net/yogarine/eclipse/ubuntu **[COLOR="red"]YOUR_UBUNTU_VERSION_HERE[/COLOR]** main 
```

See those bold, red letters? Enter either **jaunty** if you are using 9.04 and **karmic** if you are on 9.10.

Now save the file and close that window.

In your still open terminal:

```
wget http://www2.yogarine.com/eclipse-ppa.key -O- | sudo apt-key add -
```

hit Enter

OK - now in terminal:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade

```

then finally:

```
sudo apt-get install eclipse
```

Yer now a L33T hacker, dude.

---

### Post by steveneddy on 2010-01-14
> **Enigmapond said:**
> right...do the above and then follow this tutorial,,,
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

This is a great reference site for education, but adding the ppa should cover the OP's issue, which is covered in your site.

I need to bookmark that site - save a lot of time.

---

