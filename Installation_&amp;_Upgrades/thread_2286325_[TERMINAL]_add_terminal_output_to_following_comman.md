---
title: "[TERMINAL] add terminal output to following command"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by cookie-crisp on 2015-07-11
Hi there,
I tried to write something like a script to make the re-installation of Ubuntu easier.

First of all I was wondering if it's possible to add content of ```
ftp://download.nvidia.com/XFree86/Linux-x86_64/latest.txt
``` to ```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/**content of latest.txt**
``` so that the output would be like this in this case:

```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/352.21 352.21/NVIDIA-Linux-x86_64-352.21.run
```

This would give me the chance to get the latest graphics driver without looking it up.
Maybe like this: 

```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/latest.txt
```
read latest.txt
the output would be:
```
NVIDIA-Linux-x86_64-352.21.run
```
and add the output to
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/**output**
```.

I hope you can help me.
Phil

---

### Post by Lars Noodén on 2015-07-11
You could try [command substitution](http://mywiki.wooledge.org/BashFAQ/082), if you are using Bash.  

```

wget "ftp://download.nvidia.com/XFree86/Linux-x86_64/$([color=blue]wget -q -O - ftp://download.nvidia.com/XFree86/Linux-x86_64/latest.txt[/color] | [color=green]sed -e 's/^.* //; s/\;.*$//; s/\$.*$//' [/color])"

```

There, [wget](http://manpages.ubuntu.com/manpages/trusty/en/man1/wget.1.html) is run with the -q option to quiet unnecessary output and the contents of the downloaded file is redirected to stdout.  That gets piped in to [sed](http://manpages.ubuntu.com/manpages/trusty/en/man1/sed.1.html) which erases everything up to the space and if there is a semicolon or dollar sign erases anything after it to prevent shell escapes.  Then all of that ends up as an option for another instance of wget.

Hopefully there are no mistakes in that.  How are you getting notified that there is something new to download?

---

### Post by cookie-crisp on 2015-07-11
> **Lars Noodén said:**
>   How are you getting notified that there is something new to download?

The text file is called 'latest.txt' and contains the latest driver-version so I assumed that when there will be an update they will change the latest.txt-file and so the command will be 'up-to-date'.
I hope that was clear. :)

By the way, the command works pretty well, thank you.

I know that the following has nothing to do with the general topic but: Is there a possibility to automatically agree to License Agreements and so on when you're trying to install e.g. Wine?

---

### Post by Lars Noodén on 2015-07-13
Ok. I understand now.  I was considering whether you just wanted to download the latest that happens to be available at the time you need to download, or if you were wanting to get notified when the latest was available for download.  

About the licenses, I'm not sure.  The only thing I can thing of would be to use apt-get with the -y option but that might not work depending on how the license approval is queried.

---

### Post by cookie-crisp on 2015-07-13
Thanks for your answer. The -y command I already knew. But thanks anyway.

---

