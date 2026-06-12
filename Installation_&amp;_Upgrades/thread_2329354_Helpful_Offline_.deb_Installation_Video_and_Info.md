---
title: "Helpful Offline .deb Installation Video and Info"
date: 2016-06-30
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2016-06-30
If you are using (or testing) a Linux operating system and you don't have a convenient internet connection, you can still download your files from an internet-ready computer elsewhere and store the files on a flash drive.  

The easiest way to do this is explained here:

[https://www.youtube.com/watch?v=CaJWrKyLUw0](https://www.youtube.com/watch?v=CaJWrKyLUw0)

And if you don't already have Synaptic Package Manager,
from a Command Line Interface Console/Terminal, type this:  

sudo apt-get --install-suggests --install-recommends --download-only install synaptic
(the "--download-only" part is optional for the offline storage part explained below)

It's also worth knowing that you can do stuff like:  

sudo apt-get clean
sudo apt-get --install-suggests --install-recommends --download-only install gdebi

This will clear out the download cache, and then download gdebi package manager without actually installing it.  

On Ubuntu Studio, you can find the downloaded debian archives here:  

/var/cache/apt/archives/

You can then select them, copy them, and then paste them into your flash drive directory.  

Then at your offline DAW computer, you can copy the files into a new folder within your home documents area and then do this:  

sudo dpkg -i *.deb

This will attempt to install all of the debian archives found in that directory all at once.  

On Ubuntu Studio v16.04.x LTS, you may need to know how to do this because the Gnome-Software utility doesn't work quite right yet (early summer 2016), and Ubuntu Software Center has been discontinued.  

But installing Synaptic and gDebi is a good workaround.  

I hope this helps.  Peace

---

### Post by yoshii on 2016-06-30
you can type "man apt-get" to get explainations of the apt-get parameters.  
But basically the "--install-recommends" part helps to download needed dependencies.  
I included the "--install-suggests" part to include just a little bit more in case the previous part isn't enough.  
But sometimes "--install-suggests" includes a bit too much, so you might have to remove some of that stuff.  
You can simply omit the "--install-suggests" part from the command and possibly still be OK.  

And remember, you can select text from the command line and right-click the selection and do "copy text" for pasting elsewhere.  
This comes in handy when the apt-get gives you error info about what it needs.  

I hope this helps.

---

