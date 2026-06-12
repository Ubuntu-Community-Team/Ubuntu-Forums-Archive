---
title: "just installed 7.10, synaptic wont install anything else"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by beg4mercy on 2007-12-19
I can barely install anything other than ubuntu 7.10 and the 145 odd uprgades it recomended.

Its doesnt allow it, its as if some vital files are missing or something.

Basically I want to play movies, so when I try to run an mpeg or wmv it wants a codec, i try to install the codec and get this message (on totem movie player)
 
"This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

And thats the only option codec-wise that it gives me. I could list a thousand other programs that wont install but if we strart here I might be able to sort it out on my own.

I am a newbie too, so understand that I dont klnow much.

thankyou, i hope you can help, please dont say re-install  ubuntu i think me and my computer would cry.

---

### Post by forestpixie on 2007-12-19
can you do these separately in a terminal in a terminal and post the output

```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly
cat /etc/apt/sources.list
```

---

### Post by overdrank on 2007-12-19
> **beg4mercy said:**
> I can barely install anything other than ubuntu 7.10 and the 145 odd uprgades it recomended.

Its doesnt allow it, its as if some vital files are missing or something.

Basically I want to play movies, so when I try to run an mpeg or wmv it wants a codec, i try to install the codec and get this message (on totem movie player)
 
"This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

And thats the only option codec-wise that it gives me. I could list a thousand other programs that wont install but if we strart here I might be able to sort it out on my own.

I am a newbie too, so understand that I dont klnow much.

thankyou, i hope you can help, please dont say re-install  ubuntu i think me and my computer would cry.

Hi and maybe these links will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by beg4mercy on 2007-12-21
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


That was what it said after pasting what you wrote into the terminal. I will have a look at those links and get back to you thankyou

---

