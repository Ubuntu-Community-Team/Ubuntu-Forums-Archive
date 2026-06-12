---
title: "E: Malformed entry 54 in list file /etc/apt/sources.list (Component)"
date: 2016-12-21
forum: Installation &amp; Upgrades
---

### Post by janskiii on 2016-12-21
Error message appears when attempting to install new programs and 
sudo apt-get update

E: Malformed entry 54 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.

Also, in conjunction with this message in Terminal, there is the British road symbol for 'no entry' on my task bar.

I have already browsed the couple of relevant posts about this, without any success. Though this may be due to my inexperience with Ubuntu. 

I have a feeling that this is a result of an unsuccessful attempt to install Skype a couple of weeks ago.

Otherwise Ubuntu is great!!

---

### Post by papibe on 2016-12-21
Hi janskiii. Welcome to the forum ):P

Could you open a terminal, run this command and post back the results? (you can copy/paste the text from the terminal using the mouse):
```
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Please use CODE tags around the text you're gonna paste :D

Regards.

---

### Post by janskiii on 2016-12-22
Thank you for your helpfulness. Here are the results, hopefully they make some sense to you doc:


```
/etc/apt/sources.list.d/xenial-partner.list

     1	# channel for the xenial (16.04) partner channel
     2	# 
     3	#:description:This channel contains the partner software for xenial
     4	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


/etc/apt/sources.list


     1	# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
     6	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    11	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team, and may not be under a free licence. Please satisfy yourself as to
    15	## your rights to use the software. Also, please note that software in
    16	## universe WILL NOT receive any review or updates from the Ubuntu security
    17	## team.
    18	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
    19	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
    20	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
    21	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
    22	
    23	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24	## team, and may not be under a free licence. Please satisfy yourself as to 
    25	## your rights to use the software. Also, please note that software in 
    26	## multiverse WILL NOT receive any review or updates from the Ubuntu
    27	## security team.
    28	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
    29	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
    30	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    31	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    32	
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    39	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    46	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    47	
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    49	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    51	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    52	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    53	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    54	deb [http://archive.canonical.com/](http://archive.canonical.com/) xenialpartner
    55	# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenialpartner
    56	deb http.//archive.canonical.com/ xenialpartner
    57	# deb-src http.//archive.canonical.com/ xenialpartner
    58	deb [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
    59	# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
    60	# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner



```

---

### Post by papibe on 2016-12-22
Thanks.

There's should be an space between the words xenial and partner:
```
54	deb http://archive.canonical.com/ xenialpartner
```
To change it, open a editor as root:
```
sudo nano /etc/apt/sources.list
```
Go to the line, and edit it so it looks like this:
```
deb http://archive.canonical.com/ xenial partner
```
Save the file, and see what happens.

You may have a duplicate line, same one, with a line on /etc/apt/sources.list.d/xenial-partner.list, see what is happening [here]("https://ubuntuforums.org/showthread.php?t=2347122") to fix that.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by deadflowr on 2016-12-22
Since you have the /etc/apt/sources.list.d/xenial-partner.list file and it is what you want,
you might as well simply comment (#) out the lines in the sources.list file for 54, 56 and 58
54 and 56 are wrong anyway and 58 duplicates the line in the other file, mentioned above.

Easy edit is to open text editor (I prefer nano, others like vi or other editors), as root
something like
```
sudo nano /etc/apt/sources.list
```
scroll down to the end where those lines are and add a # symbol to the end.
This marks the line as not to be read, or in layman's terms disables the line.

Then press ctrl + X to save and exit
(Press ctrl + X then press y to except the changes and enter will save the file; after you hit Y for yes to except the changes the filename will appear so you can review it. Normally ,unless you decided to play Beethoven on your keyboard, the file name will be the exact same as it was, so in that case, simply hit enter.)

If that make snese.

After you edit, re-run
```
sudo apt-get update
```
and see if the error still persists.

Hope it helps

Ninja'd

---

### Post by ajgreeny on 2016-12-22
The question is surely, how and why did the partner repos appear as a separate entry in /etc/apt/sources.list.d and not just as a line in /etc/apt/sources.list as it normally does.

This seems a bit reminiscent of the problem I had with the proposed repos appearing suddenly as an entry in /etc/apt/sources.list.d with no action from me to enable them, as I noted and queried in the thread at [https://ubuntuforums.org/showthread.php?t=2346590](https://ubuntuforums.org/showthread.php?t=2346590)

---

### Post by janskiii on 2016-12-23
papibe:
Thank you for the speedy response. Since inserting the space in the line, so it reads:

```
[COLOR=#000000][FONT=&quot]deb http://archive.canonical.com/ xenial partner[/FONT][/COLOR]
```

Terminal started expressing a different error:

```
E: Malformed entry 56 in list file /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
```

As you suggested in the related thread that you shared, I tried removing the file by using:

```
sudo rm /etc/apt/sources.list.d/xenial-partner.list
```

Alas, still experiencing 'Malformed entry 56'.

deadflowr, this is when I moved onto your advice, inserting # at the end of lines 54, 56 and 58 so they read

```
deb http://archive.canonical.com/ xenial partner #
deb http.//archive.canonical.com/ xenialpartner #
deb http://archive.canonical.com/ xenial partner #




```

Still no success, after running 

```
sudo apt-get update
```

Ubuntu is still experiencing
```
E: Malformed entry 56 in list file /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
```

Thank you for your help hitherto! What do you think about this next stage of the problem?

Peace

---

### Post by howefield on 2016-12-23
It is the same issue in line 56 as you had in line 54, there are a few lines in fact which need a space or commenting out.

The # symbol needs to be added to the beginning of the line.

---

### Post by janskiii on 2016-12-23
howefield,

That was the final piece of this jigsaw. I inserted spaces between 'xenial' and 'partner'. Also I added the '#' to the beginning of lines 54, 56 and 58. Since then I have run successful 
sudo apt-get update
as well as installing a few programs and updates.

Thank you, papibe, deadflowr, ajgreeny and howefield for you combined help, my computer is functioning again. All the best to you all.

---

### Post by howefield on 2016-12-23
> **janskiii said:**
> Since then I have run successful ....

Cool, well done and feel free to mark the thread as solved if you wish.

---

