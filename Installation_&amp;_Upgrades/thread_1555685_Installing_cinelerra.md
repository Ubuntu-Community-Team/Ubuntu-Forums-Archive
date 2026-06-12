---
title: "Installing cinelerra"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by Waldvogel on 2010-08-18
Have been to the website of cinelerra but cannot for the life of me work out how to install the programme.
Any help would be most cordially appreciated.

---

### Post by ronnielsen1 on 2010-08-18
Click on the link below (The one in the quote) and open with gdebi
> Installation notes:
- For your convenience you can install a package for detecting your  version of Ubuntu, installing akirad repository and keeping it updated.
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer.[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by ronnielsen1 on 2010-08-18
The link I gave you did add the repo to my sources list but there were no packages for maverick so I edited the sources in synaptic and changed maverick to lucid and it worked

---

### Post by Waldvogel on 2010-08-18
Clicked on the link thanks and downloaded it thanks.
Now there's something on my background called addakirad.deb. I have no idea how that links with getting cinelerra.

'but there were no packages for maverick so I edited the sources in synaptic and changed maverick to lucid and it worked'
Likewise I am lost at trying to understand this ^.

Some background-I use Windows Vista but want to do some video editing, installed ubuntu with the understanding that cinelerra is a good programme + that it's very easy to install things on ubuntu.

---

### Post by Waldvogel on 2010-08-18
Please help! I beg you!
This is your chance to make ubuntu look like it's actually sensible and not ridiculously complicated to get anyhting done...I don't want to have to buy software for windows :P

---

### Post by ronnielsen1 on 2010-08-18
Let me work on it and I'll try to provide you with a deb (Ubuntu's equivalent of an exe for windows)

Software can be easy to install in linux. There is a learning curve. Some software is not as easy to install as it is in windows but in the end, you can have all the apps you want and a very secure system where nothing is hid from you

It's late here. I'll check in the morning

---

### Post by ronnielsen1 on 2010-08-19
> Please help! I beg you!
This is your chance to make ubuntu look like it's actually sensible and  not ridiculously complicated to get anyhting done...I don't want to have  to buy software for windows Some things are harder to install than Windows. Sorry. It's getting easier than it used to be. It's worth it after you figure it out. Some things come in a nice deb file that you just click on. Not everyone provides a deb file (Google, for one) but do provide a linux compatible package.
I think it might have worked for you. Go to [COLOR=Blue]System > Administration > Synaptic Package Manager[/COLOR]

When it opens check to see if Cinelerra is an option to install


 If not then close Synaptic and do the following:

Navigate to [COLOR=Blue]Applications > Accessories > Terminal[/COLOR]

 When it opens copy and paste the following text in the terminal

```
wget -q http://akirad.cinelerra.org/pool/addakirad.deb &&  sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo  apt-get update
```

This will download a package with wget, install it that will  detect your version of Ubuntu you're running and add the repositories that you need in order to stay current with the program. 

When it finishes, close the terminal and reopen Synaptic and search for cinelerra

If you're successful, here's another program you might be interested in.

[http://www.ubuntugeek.com/install-openshot-video-editor-1-1-in-ubuntu-10-04-lucid-9-10-karmic.html](http://www.ubuntugeek.com/install-openshot-video-editor-1-1-in-ubuntu-10-04-lucid-9-10-karmic.html)

---

### Post by Waldvogel on 2010-08-19
Followed your instructions and they were spot on. I now have cinelerra installed.

One thousand thank yous for your help, you're a knight of the internet!

---

### Post by ronnielsen1 on 2010-08-20
Great! Did you look at the other software?

> If you're successful, here's another program you might be interested in.

[http://www.ubuntugeek.com/install-op...10-karmic.html]("http://www.ubuntugeek.com/install-openshot-video-editor-1-1-in-ubuntu-10-04-lucid-9-10-karmic.html")

---

