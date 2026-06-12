---
title: "JMF - I can't Install it!!!"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by Jamezo97 on 2010-09-30
Hi all,
I'm a noob, i'll just say that from the start.
Anyway, I have a program called Mercury, which allows you to do voice chats, over a MSN type interface. So i installed the program, ran the program, logged in, clicked on the "Start a voice chat" button, and it came up with an error saying that it can't find JMF. So I looked up what JMF is, and found out that it is "Java Media Framework". So I followed the instruction, on how to install it from the website: "http://wiki.services.openoffice.org/wiki/Java/Java_Media_Framework" I got down to the step where it says :> Type yes to accept it. You will be asked with two more questions. Answer no to them: and I did that, but then it came up with this error:
> Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.2415: 1: cannot open ==: No such file
./install.sfx.2415: 1: ==: not found
./install.sfx.2415: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
Done.I had a look on the internet, and tried this:
[http://wiki.services.openoffice.org/wiki/Java/Java_Media_Framework#Troubleshooting](http://wiki.services.openoffice.org/wiki/Java/Java_Media_Framework#Troubleshooting)

and I also read somewhere, that if you rename the file, to a .zip, then extract it, it will come up with an error, but still extract the files. Then you recompile it, rename it back to a .bin and it should all work.

Neither of those work for me, and it always keeps coming up with the same error.


Any help on this Situation, would be great.
(P.S.: I am a noob, so if you find a way to fix it, please don't talk tech, just simple command codes and stuff. Thanks)

---

### Post by Jamezo97 on 2010-09-30
Oh, Never Mind, I managed to install it. It's annoying, I spend hours trying to work something out, then I post a forum topic, and then I figure out how to do it straight away.
I tried to do the vim thingie again, and somehow it worked. I got the .bin file, and put it in a folder called JMF on my desktop, then I cd to the folder and did the steps in the 5th post here:
[http://ubuntuforums.org/archive/index.php/t-1137722.html](http://ubuntuforums.org/archive/index.php/t-1137722.html)

Or just follow these steps:
> 1 - Erase any jmf.bin file that you had download. Download a new one and put in a folder, and check file size:

ls -l

This is a probably result:
-rwxr-xr-x 1 nobody nogroup 2419679 2009-03-07 11:52 jmf-2_1_1e-linux-i586.bin

filezise: 2419679 bytes

2 - Give permission to file:
chmod +x jmf-2_1_1e-linux-i586.bin

THIS IS THE MOST IMPORTANT STEP
3 - Edit jmf-2_1_1e-linux-i586.bin downloaded file with vim as root
vim -b jmf-2_1_1e-linux-i586.bin (YOU HAVE TO USE THIS COMMAND -b BECAUSE IT'S A BINARY FILE)

4 - At vim type this:
/tailPress ENTER.

Then press the key l to move to the left on that line, until the sign +.

Press i to insert text, and insert -n , with a space. Press ENTER.

The new line should be like this:
tail -n +309 $0 > $outname
5 - Now press ESC and type:
:wqPress ENTER.
6 - Now execute the jmf bin file.

That's it.

I uploaded the edited file to here:
[http://download472.mediafire.com/19ljiuvdtmig/fzd9ug4glddreho/jmf-2_1_1e-linux-i586.bin](http://download472.mediafire.com/19ljiuvdtmig/fzd9ug4glddreho/jmf-2_1_1e-linux-i586.bin)

---

### Post by frankvdh on 2010-12-07
Thanks Jamezo97 -- saved me a heap of problems!!!! 

One little error in your post...

Your line
> Press i to insert text, and insert -n , with a space. Press ENTER.
shouldn't have "press ENTER." i.e. it should read

> Press i to insert text, and insert -n , with a space.

---

### Post by Lord_JABA on 2012-04-01
Followed the instructions above. Now i get:
```

Unpacking...
Extracting...
./jmf-2_1_1e-linux-i586.bin: 297: ./install.sfx.26485: not found

...


```
please help.

EDIT: number after ./install.sfx is different every time I try

---

