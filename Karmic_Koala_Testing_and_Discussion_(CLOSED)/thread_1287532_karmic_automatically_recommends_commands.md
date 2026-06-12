---
title: "karmic automatically recommends commands?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sandyd on 2009-10-10
I just found this out when i typed
```

gamp

```
instead of 
```
 gimp
```

it showed
```

dolphinaura@dolphinaura-laptop:~$ gamp
No command 'gamp' found, did you mean:
 Command 'gamt' from package 'gamt' (universe)
 Command 'gimp' from package 'gimp' (main)
 Command 'gap' from package 'gap-core' (universe)
gamp: command not found
dolphinaura@dolphinaura-laptop:~$


```

nice huh?

---

### Post by slakkie on 2009-10-10
I take it you run bash.

For the heck of it, run, sudo aptitude remove command-not-found

Then do it again, see how it behaves.
Install the package again.

In zsh i have this:

```

ssudo aptitude changelog kdm
zsh: correct 'ssudo' to 'sudo' [nyae]? y
Get:1 ChangeLog of kdm [100kB]
Fetched 100kB in 0s (231kB/s)

```

---

### Post by Screwdriver0815 on 2009-10-10
thats nice, indeed.

Another reason for Karmic 
(I am collecting reasons right now, to get a decision: switch? yes, or no? until the end of this month)

this feature makes the system still more human than it was before

---

### Post by coldReactive on 2009-10-10
Actually Jaunty has this slightly too now after all the updates.

Oh no wait, it's that "you could've meant more than one package" message, even though you typed the name right.

---

### Post by madjr on 2009-10-10
cool:guitar:

---

### Post by FuturePilot on 2009-10-10
Ubuntu has been doing this for a long time. I think they just slightly reworded it in Karmic.

---

### Post by Screwdriver0815 on 2009-10-10
> **FuturePilot said:**
> Ubuntu has been doing this for a long time. I think they just slightly reworded it in Karmic.
I don't have this in Jaunty and I also don't know it from the other systems (Hardy and Intrepid).

when you do a typo in the terminal it always answers with 

```
command not found
```

---

### Post by sisco311 on 2009-10-10
> **Screwdriver0815 said:**
> I don't have this in Jaunty and I also don't know it from the other systems (Hardy and Intrepid).

when you do a typo in the terminal it always answers with 

```
command not found
```

command-not-found is installed by default in Ubuntu since Hardy.

it suggest installation of packages in interactive bash sessions. the package will install handler for command_not_found that lookups programs not currently installed but available from the repositiories.

i.e.:
```
sisco@acme:~$ tvtime
The program 'tvtime' is currently not installed.  You can install it by typing:
sudo apt-get install tvtime
tvtime: command not found

```

spelling correction was added in version 0.2.36:
> [noparse]command-not-found (0.2.36ubuntu1) karmic; urgency=low

  * scan.data: updated to current karmic
  * scan.data: add exception for gftp (LP: #99708)
  * debian/postinst:
    - if old/leftover /etc/bash_command_found_found is there,
      remove it (LP: #379851)
  * debian/rules:
    - build with DH_PYCENTRAL=include-links LP: #342003
  * CommandNotFound/util.py:
    - use try gettext if lgettext fails (LP: #282446)
  * debian/copyright: 
    - fix location (LP: #314478)
  * CommandNotFound/CommandNotFound.py:
    - be more robust about missing priority.txt (LP: #359784)[/noparse]
    - **add simple spelling correction (LP: #314486)**[noparse]
  * debian/control:
    - build for all python versions (LP: #366096)

 -- Michael Vogt <michael.vogt@ubuntu.com>  Fri, 26 Jun 2009 13:58:24 +0200[/noparse]

---

### Post by FuturePilot on 2009-10-10
> **Screwdriver0815 said:**
> I don't have this in Jaunty and I also don't know it from the other systems (Hardy and Intrepid).

when you do a typo in the terminal it always answers with 

```
command not found
```

Never mind, I see what they did. This is new. Previously if you entered an actual command but the package wasn't installed (say you entered "gimp" but gimp wasn't installed) it would tell you what package the command was in. But now it's  a little smarter. However Zsh has done this since forever. Bash playing catch-up again :p

---

### Post by sisco311 on 2009-10-10
> **FuturePilot said:**
> Bash playing catch-up again :p

it's not a bash feature. bash still returns *command not found*

```
sisco@acme:~$ tvtime
The program 'tvtime' is currently not installed.  You can install it by typing:
sudo apt-get install tvtime
**tvtime: command not found**
```

---

### Post by FuturePilot on 2009-10-10
> **sisco311 said:**
> it's not a bash feature. bash still returns *command not found*

```
sisco@acme:~$ tvtime
The program 'tvtime' is currently not installed.  You can install it by typing:
sudo apt-get install tvtime
**tvtime: command not found**
```

Well, whatever it is Zsh has a suggestion feature built right in to it and it's much superior. Yes, I'm a Zsh nut :twisted:

---

### Post by toupeiro on 2009-10-10
hmmmm, maybe thats why the shell is so huge (for a shell).  But seriously, you wouldn't even notice from the 425Mb firefox process. :P

---

### Post by arrange on 2009-10-10
```
arrange@lean ~$ gimp
Your spelling seems correct, and gimp IS installed, but did you really mean gimp?
Didn't you want to launch gap, gip, or gwp instead? [Yn] n

OK, launching gimp then... 
```

:)

---

### Post by sisco311 on 2009-10-10
> **arrange said:**
> ```
arrange@lean ~$ gimp
Your spelling seems correct, and gimp IS installed, but did you really mean gimp?
Didn't you want to launch gap, gip, or gwp instead? [Yn] n

OK, launching gimp then... 
```

:)

version 0.2:
```
arrange@lean ~$ gimp
Your spelling seems correct, and gimp IS installed, but did you really mean gimp?
Didn't you want to launch gap, gip, or gwp instead? [Yn] n
Are you sure? [yN] y
OKAY, please press any key to continue... 
OK, launching gimp then...

fatal error: evilmalware not installed

Do you want to install evilmalware?  [Y] n

error: n is not recognized as an option.

Do you want to install evilmalware?  [Y]
```

---

### Post by blueturtl on 2009-10-10
```
arrange@lean ~$ gimp

It looks like you're trying to write a letter.
Would you like me to launch OpenOffice for you? [Y/n]n

How about a nice sudo rm -rf / ? [Y/n]
```

---

### Post by RaZe42 on 2009-10-10
Leave Clippy alone! :D

---

### Post by arrange on 2009-10-10
```
arrange@lean ~$ gimp

It looks like you're trying to write a letter.
Would you like me to launch OpenOffice for you? [Y/n]n

How about a nice sudo rm -rf / ? [Y/n]n

2 system suggestions refused. This incident will be reported.

Falling back to the last command suggested.

sudo rm -rf /
[sudo] password for arrange:
```

---

