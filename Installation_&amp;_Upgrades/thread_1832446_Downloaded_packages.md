---
title: "Downloaded packages"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by Ginzell on 2011-08-24
Hi Friends,
Is there any way to find out what packages are on my laptop but aren't installed yet?
  
For instance, I downloaded a tarball and inside were many files (obviously) and in my research I came across someone posting - to find out if java installed type cmd javac -version.  When I typed that it showed me several packages that it found that needed to be installed.  So what I was wondering is, is there a command that looks through my entire HD and finds all packages available that haven't been installed yet.
I tried looking through synaptic for this because it looked as though there was a filter for it there, but I'm either doing it wrong, or it's not what I'm looking for.  

Thanks,

---

### Post by dave01945 on 2011-08-24
as far as i'm aware if you install programs from source you need to keep track of them synaptic only deals with packages one way to get synaptic to keep track of programs installed from source is to use

```
checkinstall
```

rather than make install but if you haven't installed it yet then it is just a file or tarball you could search for files ending in tar.gz, etc but there are a few of them on the system anyway and it won't tell you if it's installed

prob the best thing to do is put all source you download into the same directory and don't download unless you plan to install it

also anything you download through synaptic or apt-get is stored in

```
/var/cache/apt/archives/
```

but if you downloaded them it probably installed them too

---

### Post by Ginzell on 2011-08-24
Hi,
I do know where it downloaded to, a better way to word my question is which file do I use to install. Or how do I know which package file to use.

Here's my reasoning behind all this, although flawed it may surely be. 
I started by downloading java jdk 7 tarball. (paraphrasing names) I didn't know which file to point to (after unzipping) to install it either, so I searched around on the forums.  Someone said to check to see if it was installed by typing javac -version.  I did, just to see what would come up.  It showed several packages that it said needed to be installed.  I picked the first one, installed it from terminal and it installed the other packages that were listed too.  So when I downloaded Android SDK, I thought to do it the same way, only I had no name to go by to put "-version" with.  There wasn't really any particular reason I chose to do the javac -version cmd, however I did get info from it.  So my thinking was that if I could just get a list of packages that were in the tarball (unzipped) that needed to be installed I could go from there.
I'm doing all this in VBox so it didn't really matter if it went south.  (although that's not what I wanted)  
I find that if I research to the fullest extent whatever I'm doing, that I learn more from it.  I'm not real familiar with how to do all installs from terminal yet with Ubuntu, I've done several .deb files but most of the sites will give details on how to install something.  However I am unable to find anything on this SDK.  (I take that back, I found plenty on the site, just not details on how to install (yet). So far just "Install this and that")
Still searching..

---

### Post by dave01945 on 2011-08-24
usually if it's a tarball after you have extracted it it usually makes a folder in the same directory as the tarball under the same name just without tar.gz at the end to install (most) you open up the terminal and cd to that new directory then type

```
./configure
make
sudo checkinstall
```

there are alot of posts on the internet about installing tarballs just google install tar.gz

but for most programs unless there is a special need to get the source straight from the developer you can use synaptic

---

### Post by Ginzell on 2011-08-24
Ok I think I found it.  I still can't get used to this frontend backend thing going on with linux, but that's what this is I think.  I had to run the SDK manager and it allows me to install more stuff.  
I'll do that and see where it takes me.
I'm still curious to know the answer to my question though, if anyone knows, how to list packages that haven't been installed yet on your HD.  Let's just say if someone used my laptop and downloaded a bunch of packages all over the place but didn't know how to install them, how could I find out what packages where there.

thanks!

---

### Post by oldos2er on 2011-08-24
If you know the package name, ```
aptitude show <package>
``` will show if it's installed or not. So will ```
dpkg-query -s <package>
```

---

