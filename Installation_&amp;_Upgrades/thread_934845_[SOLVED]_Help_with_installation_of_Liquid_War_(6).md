---
title: "[SOLVED] Help with installation of Liquid War (6)"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by arkticcool on 2008-10-01
[COLOR="Red"]IF YOU WANT TO GO DIRECTLY TO THE SOLUTION ITS ON THE SECOND PAGE[/COLOR]

I have downloaded the beta version of Liquid war, liquidwar6-0.0.4beta.tar.gz, which can be found at; [http://download.savannah.gnu.org/releases/liquidwar6/0.0.4beta/liquidwar6-0.0.4beta.tar.gz]("http://download.savannah.gnu.org/releases/liquidwar6/0.0.4beta/liquidwar6-0.0.4beta.tar.gz")

There is an installation guide here, but I can't make neither head nor tail out of it; [http://http://www.gnu.org/software/liquidwar6/manual/liquidwar6.html#Installation]("http://http://www.gnu.org/software/liquidwar6/manual/liquidwar6.html#Installation")

I just got linux and so have no idea how to compile programs as it says in the manual. I also have no idea how to install librarires.

A list of code on how to install would be greatly appreciated as would links to help/tutorials.

Thank you in advance.

---

### Post by Partyboi2 on 2008-10-01
Open a terminal (Applications>Accessories>Terminal) and install build-essential package and a few others you will need to compile liquid wars
```
sudo apt-get install build-essential libgmp3-dev guile-1.8-dev libsdl-ttf2.0-dev libsdl-mixer1.2-dev
``` Once these have been installed change to where the downloaded liquidwar6-0.0.4beta.tar.gz file is. So if its on your Desktop you would type
```
 cd ~/Desktop
``` then extract it with
```
tar xvzf liquidwar6-0.0.4beta.tar.gz
``` then cd into the newly made directory
```
cd liquidwar6-0.0.4beta
``` then type
```
./configure
``` If this finishes without errors then use
```
make
``` If that passes without errors then install with
```
sudo make install
```If you are wanting a more stable version then you can install the version in the ubuntu repo's with
```
sudo apt-get install liquidwar
```

---

### Post by arkticcool on 2008-10-01
I've installed the libs, first step, without a hitch, all are installed. However the ./configure command doesn't work, do I change that command to the file name or something, because the only thing I got back after the installation was;
```
bash: ./configure: No such file or directory
```
doesn't work if I sudo it either
```
sudo: ./configure: command not found
```
Probably an extremely newbie mistake, but I don't know what I'm doing wrong.

---

### Post by Partyboi2 on 2008-10-02
> **arkticcool said:**
> I've installed the libs, first step, without a hitch, all are installed. However the ./configure command doesn't work, do I change that command to the file name or something, because the only thing I got back after the installation was;
```
bash: ./configure: No such file or directory
```doesn't work if I sudo it either
```
sudo: ./configure: command not found
```Probably an extremely newbie mistake, but I don't know what I'm doing wrong.
Sorry me bad I forgot a few steps. I have fixed my previous post, so follow it through again.

---

### Post by arkticcool on 2008-10-02
Thank you for the speedy reply.

I got to the point where I've cd to the directory, and have typed in ./configure. However one error occurs, it states the following;

```
checking for expat.h... (cached) no
configure: error:
*** Liquid War 6 needs Expat (http://www.libexpat.org/)

```

I've gone to synaptic package manager, to look for expat. However, there are a variety off packages and I don't know which to install, or whether I should download and install from the site.

---

### Post by Partyboi2 on 2008-10-02
Try installing libexpat1-dev, so type
```
sudo apt-get install libexpat1-dev
```
then run ./configure again.
[B]
[/B]

---

### Post by arkticcool on 2008-10-02
Thanks once again for the fast reply.

I configured again, and the expat error did not arise.

However it looks like a need a few more libraries.

```
checking curl/curl.h usability... no
checking curl/curl.h presence... no
checking for curl/curl.h... no
configure: WARNING:
*** Liquid War 6 recommends libcURL (http://curl.haxx.se/libcurl/)

checking for curl_global_init in -lcurl... no
configure: WARNING:
*** Liquid War 6 recommends libcURL (http://curl.haxx.se/libcurl/)

checking sqlite3.h usability... no
checking sqlite3.h presence... no
checking for sqlite3.h... no
configure: error:
*** Liquid War 6 needs SQLite 3 (http://www.sqlite.org/)

```

Which packages should I install?

---

### Post by Partyboi2 on 2008-10-02
Install libsqlite3-dev package and run ./configure again.
```
sudo apt-get install libsqlite3-dev
```

---

### Post by arkticcool on 2008-10-02
Had a few more errors with missing libs, but as you stated above, I simply went to synaptic package manager and installed the -dev versions. Went through ./configure without problem, make and sudo make install.

Now one last noobish question, how do I open it/where is it.

---

### Post by Partyboi2 on 2008-10-02
you should be able to start the game by typing in a terminal
```
/usr/local/games/liquidwar
```

---

### Post by arkticcool on 2008-10-03
Installed some of the optional libraries, as many as I thought necessary. The executable is created in the actual folder. I have executed it. A black screen comes up. However there are a variety of other "test" executables within the folder, that prove that the graphics and sound work. What library do you think I'm missing.

---

### Post by arkticcool on 2008-10-06
Solved this. Install all the libs, optional/req'd, devleoper versions through synaptic package manager then download the liquid war tar.gz and follow partboi2's instructions below.

Re: Help with installation of Liquid War (6)
Open a terminal (Applications>Accessories>Terminal) and install build-essential package and a few others you will need to compile liquid wars
Code:

```
sudo apt-get install build-essential libgmp3-dev guile-1.8-dev libsdl-ttf2.0-dev libsdl-mixer1.2-dev
```

Once these have been installed change to where the downloaded liquidwar6-0.0.4beta.tar.gz file is. So if its on your Desktop you would type
Code:

```
 cd ~/Desktop
```

then extract it with
Code:

```
tar xvzf liquidwar6-0.0.4beta.tar.gz
```

then cd into the newly made directory
Code:

```
cd liquidwar6-0.0.4beta
```

then type
Code:

```
./configure
```

If this finishes without errors then use
Code:

```
make
```

If that passes without errors then install with
Code:

```
sudo make install
```

If you are wanting a more stable version then you can install the version in the ubuntu repo's with
Code:

```
sudo apt-get install liquidwar
```

thanks to partyboi2.

---

