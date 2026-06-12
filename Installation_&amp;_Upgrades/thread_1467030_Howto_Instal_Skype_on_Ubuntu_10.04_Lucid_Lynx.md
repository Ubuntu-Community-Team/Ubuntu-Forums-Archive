---
title: "Howto: Instal Skype on Ubuntu 10.04 Lucid Lynx"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by jonathank89 on 2010-04-30
This is basically the same install process for 9.10. I didn't run into any trouble after installing Skype on several different machines, this is of course assuming that your sound input/output worked before hand and isn't muted.

Here's the [tutorial]("http://friendlytechninja.com/2010/04/30/howto-install-skype-on-ubuntu-10-04-lucid-lynx/") it's quite easy to follow and I hope people find it helpful.

[http://friendlytechninja.com/2010/04/30/howto-install-skype-on-ubuntu-10-04-lucid-lynx/](http://friendlytechninja.com/2010/04/30/howto-install-skype-on-ubuntu-10-04-lucid-lynx/)

---

### Post by latebeat on 2010-05-01
very nice, thanks

---

### Post by KegHead on 2010-07-06
Hi!

I'll try this today for my wife's compag notebook.

Thanks for the entry.

BTW my wife just got back from a month in Ireland-she loved it!

KegHead

---

### Post by crichard on 2010-07-06
For your info, Skype is avaiable in Synaptic Package Manager :)

---

### Post by KegHead on 2010-07-06
Hi!

Directions worked perfectly.

Thanks!

KegHead

---

### Post by santhosh.he on 2010-07-27
I suggest you to download .deb file from the below path and install it easily 

path : [http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/)

---

### Post by astrobob.tk on 2010-09-22
Hey there,

I've tried downloading & Installing Skype from the [website]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/") (Ubuntu 8.10 +64) but i keep getting this error
```
Error: Wrong architecture 'amd64'
```I also tried to run in the terminal:
```
sudo apt-get update && sudo apt-get install skype
```& i got:
```
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate
```I checked synaptic & there's no Skype package :(

help plz

---

### Post by minigilani on 2010-09-22
astrobob.tk, check to see if your Multiverse sources are enabled in Synaptics.

---

### Post by KegHead on 2010-09-22
Hi!

Skype is available in synaptic.

I'm using 10.04 on my desktop.

KegHead

---

### Post by astrobob.tk on 2010-09-22
> **minigilani said:**
> astrobob.tk, check to see if your Multiverse sources are enabled in Synaptics.

Do you mean if "(Multiverse)" appears in the side pane? it does.

@KegHead: I am aware of that when I was working on my other laptop, before installing Ubuntu on this new one.
Here's a screenshot of my Skype search. Am I missing something in the result ?

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6763[/IMG]

---

### Post by luissa on 2011-06-18
no skype package for me neither in ubuntu 10.4 (with updated multiverse).

am running ubuntu on a 64 bit machine.

---

### Post by astrobob.tk on 2011-09-21
> **luissa said:**
> no skype package for me neither in ubuntu 10.4 (with updated multiverse).

am running ubuntu on a 64 bit machine.

> **astrobob.tk said:**
> Do you mean if "(Multiverse)" appears in the side pane? it does.

@KegHead: I am aware of that when I was working on my other laptop, before installing Ubuntu on this new one.
Here's a screenshot of my Skype search. Am I missing something in the result ?

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6763[/IMG]

Well am not sure why I never came back  & solved this, but I used the Skype .deb & it worked perfectly until 2day.

To answer u luissa, check the repositories & make sure that "Ubuntu lucid Partner" is checked. Only then can you find Skype in the repository (of course after reploading it).

As for mycurrent problem, I will link to a new thread 2night. I will first check to pruge remove skype.

---

### Post by Hakunka-Matata on 2011-09-21
> 
Error: Wrong architecture 'amd64'


That means you have a 32bit installation, and it doesn't want any part of the 64bit Skype Package.  Download and install the 32 bit version.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by astrobob.tk on 2011-09-22
> **Hakunka-Matata said:**
> That means you have a 32bit installation, and it doesn't want any part of the 64bit Skype Package.  Download and install the 32 bit version.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)


Where can we get the "alpha" version ? I am having a problem with the beta. Just 2 days ago i started having it. It's really annoying. Check this thread for details: [http://ubuntuforums.org/showthread.php?t=1848489]("http://ubuntuforums.org/showthread.php?t=1848489")

---

### Post by Hakunka-Matata on 2011-09-22
It appears you're discussing this situation in another thread simultaneously, this is just a copy of my reply in the other thread.  Did you try the 32bit download in the Skype link?, beta 2.2 works fine for me on 10.04, 10.10, 11.04, and 11.10 beta. 

you can also open **System Monitor**, choose processes, sort on name  column, find multiple skype instances, and kill a couple.  Happens all  the time to me, sometimes the blue skype icon disappears from the top  panel, but Skype is still running, so you open a second instance, and  wham, problem.

---

### Post by astrobob.tk on 2011-09-22
> **Hakunka-Matata said:**
> It appears you're discussing this situation in another thread simultaneously, this is just a copy of my reply in the other thread.  Did you try the 32bit download in the Skype link?, beta 2.2 works fine for me on 10.04, 10.10, 11.04, and 11.10 beta. 


Well no; i just mentioned the other thread in case anyone on this thread (which is related) could help. It was not my intention to discuss in both threads.

sorry for the inconvinience though.

---

### Post by Hakunka-Matata on 2011-09-22
no inconvenience, no worries.  Did you get the problem sorted?

---

### Post by astrobob.tk on 2011-09-22
> **Hakunka-Matata said:**
> no inconvenience, no worries.  Did you get the problem sorted?

well it happened again & froze, but I sought that launching from the terminal will surely kill it using the ctrl+C, fast & easy.

---

