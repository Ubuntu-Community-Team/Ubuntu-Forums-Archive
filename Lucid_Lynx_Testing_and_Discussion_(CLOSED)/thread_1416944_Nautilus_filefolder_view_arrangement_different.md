---
title: "Nautilus file/folder view arrangement different"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-02-26
I've actually noticed this for quite a while but it's such a minor thing I've just basically overlooked it. I notice that all files/folders are now arranged like:

A-B-C-D then a-b-c-d

Whereas older versions are:

A-a-B-b-C-c-D-d

Of course in both versions anything beginning with "." comes after.

Anyway I'd think there'd be a place in gconf-editor to change that but I'll be jiggered if I can find it.

---

### Post by lidex on 2010-02-26
Your main menu. "applications>system>preferences>file management"
or nautilus window "edit>preferences"

---

### Post by kansasnoob on 2010-02-26
> **lidex said:**
> Your main menu. "applications>system>preferences>file management"
or nautilus window "edit>preferences"

I see no "applications>system>preferences>file management" ?????????? or even system>preferences>file management.

I have compared settings from my stable everyday Jaunty's Nautilus preferences to those in Lucid and made sure they're the same.

No go. I'm sure there's a setting in gconf I just haven't spent much time trying to figure it out because it's such a minor thing, but I do have some file names that begin with lower case letters and I'm used to the old behavior.

Maybe I'll try copying a Karmic gconf to Lucid and see what I blow up :D

---

### Post by lidex on 2010-02-26
Nautilus window. "Edit>Preferences" menu. See Screenshot.

---

### Post by ranch hand on 2010-02-27
The problem is a little more basic than the preferences handle.  It is how it sorts thing alpha numerically that has changed.  Set it how you like and the order will be all uper case and then all lower case.

It used to be A then a then B then b ad nausium.  The new system really screws with the file names I have come to use with the old order.

---

### Post by kansasnoob on 2010-02-27
> **lidex said:**
> Nautilus window. "Edit>Preferences" menu. See Screenshot.

Yes, I get that. I still end up with folder Jack then Jill then jack then jill. It sorts differently.

All upper case first and all lower case second.

I have tried trashing the gconf, gnome, and nautilus folders to restore the defaults and it's always the same.

---

### Post by lidex on 2010-02-27
Mine doesn't do that (Jaunty). Check the output of "locale" in terminal, specifically the value of "LC_COLLATE="

[http://ubuntuforums.org/showthread.php?t=471154]("http://ubuntuforums.org/showthread.php?t=471154")
[http://www.iac.es/sieinvens/siepedia/pmwiki.php?n=Tutorials.LinuxLocale]("http://www.iac.es/sieinvens/siepedia/pmwiki.php?n=Tutorials.LinuxLocale")
[http://www.linux.com/archive/articles/53781]("http://www.linux.com/archive/articles/53781")


Here's what I have:
```
~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
[COLOR="Red"]LC_COLLATE="en_US.UTF-8"[/COLOR]
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

```
~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

---

### Post by ranch hand on 2010-02-27
I will have to do that when I am back over on my test platform (I am running 9.04 right now myself).  I am pretty sure that it will read the same.

I am going to try compiling the bugger from source anyway because of the move of tabs to the bottom.

My big question is why are you on the 10.04-testing forum if you do not run it?

Nautilus has undergone some huge changes just recently and we are trying to get our heads around it.  The spoit view is very nice but the tabs on the bottom make up for that and then the weird reordering of the file order.  Right now it adds up to a -1.

It seems that you can recompile the bugger to move the tabs back to the top.  May be able to find the ordering part and change it too.

If you are going to join in the forum you really ought to join the FUN.

---

### Post by lidex on 2010-02-27
> **ranch hand said:**
> 
My big question is why are you on the 10.04-testing forum if you do not run it?

If you are going to join in the forum you really ought to join the FUN.

I'm just about to take the plunge. Kinda sticking my nose in to get a taste of goodies to come. This weekend I plan on dusting the kubuntu install on my second HDD to make room. ;)

---

### Post by kansasnoob on 2010-02-27
Not sure what this means but from my Jaunty:

```
lance@lance-desktop:~$ locale
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
lance@lance-desktop:~$ locale -a
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
lance@lance-desktop:~$ 

```

I'll check out all of those links a bit later.

---

### Post by ranch hand on 2010-02-27
"C" = default.  This is probably left over from some "locale" problem in the past.

If you think back there was a bug in early 9.04 having to do with that and you either had to ride it out until an update rest it at C or do it yourself.

It is also exactly what I have in 10.04.

---

### Post by VMC on 2010-02-27
> **lidex said:**
> 
...
```
~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
[COLOR="Red"]LC_COLLATE="en_US.UTF-8"[/COLOR]
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

```
~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

```
$ locale
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
[COLOR="Red"]**LC_COLLATE="en_US.utf8**[/COLOR]"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

$ locale -a
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

There's a naming difference between ***en_US.utf8*** and ***en_US.UTF-8***

---

### Post by ranch hand on 2010-02-27
Ok.

Does this mean anything in relation to getting the order restored?

The listing for my 9.04 (ordered the way I am used to) and 10.04 (ordered very differently) are exactly the same.  They both have everything a "C".   I have not checked on 9.10 as I have not been on any of them for a while.

I will do that directly.

---

### Post by sonicb00m on 2010-02-27
> **ranch hand said:**
> 

It seems that you can recompile the bugger to move the tabs back to the top.  May be able to find the ordering part and change it too.



can you explain how to do that?

---

### Post by ranch hand on 2010-02-27
> **sonicb00m said:**
> can you explain how to do that?
I have not done this completely yet.  found the line that needs editing but have not tryied the recompiling yet as there are a couple  of things I do not understand quite.

If you had searched for a nautilus thread in this forum you would have found this;

[http://ubuntuforums.org/showpost.php?p=8865200&postcount=84](http://ubuntuforums.org/showpost.php?p=8865200&postcount=84)

which should get the tabs back where they belong.

If I have success with that I may go hunting for the part that does the sorting of files.

---

### Post by seeker5528 on 2010-02-27
> **ranch hand said:**
> Does this mean anything in relation to getting the order restored?

Don't know if it means anything in relation to the sort order, but when I type in locale I get this:

```
seeker@ubuntu:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

And for me Nautilus and Dolphin both ignore case when sorting.

Regarding the LANG=C in the earlier post "C" is the fallback if the language is not set anywhere and I don't see it as an option when I go to 'Administration --> Language Support'.

Further test, I just opened a terminal window and switched to a directory that contains mixed case files in the first letter postition.

Typing 'ls' they are sorted alphabetically without regard to case.
Typing:

```
LANG=C ls
```

they are sorted 'A-Z a-z'.

EDIT: Found a link that describes the 'C' locale:

[http://docs.sun.com/app/docs/doc/817-2521/6mi67tj36?a=view](http://docs.sun.com/app/docs/doc/817-2521/6mi67tj36?a=view)

> C Locale – the Default Locale

The C locale, also known as the POSIX locale, is the POSIX system default locale for all POSIX-compliant systems. The Solaris Operating System is a POSIX system. The Single UNIX Specification, Version 3, defines the C locale. Register to read and download the specification at: [http://www.unix.org/version3/online.html](http://www.unix.org/version3/online.html).

You can specify that your internationalized programs run in the C locale, in one of two ways:

    *

      Unset all locale environment variables.

      system% unsetenv LC_ALL LANG LC_CTYPE LC_COLLATE LC_NUMERIC \
      					LC_TIME LC_MONETARY LC_MESSAGES

      Unsets all locale environment variables. Runs the application in the C locale.
    *

      Explicitly set the locale to C or POSIX.

      system% setenv LC_ALL C
      system% setenv LANG C

      Some applications check the LANG environment variables without actually calling setlocale(3C) to reference the current locale. In this case, setenv explicitly sets the C locale by specifying the LC_ALL and LANG locale environment variables. For the precedence relationship among locale environment variables, see the setlocale(3C) man page.

To check the current locale settings in a terminal environment, run the locale(1) command.

system% locale

Doesn't say anything about file sorting, but maybe that is specified elsewhere in the POSIX standard.

Later, Seeker

---

### Post by ranch hand on 2010-02-27
seeker5528
This is all your fault and I hope it works out.

I did check the Language Support deal and it claimed I didn't have it fully installed.  This is due to using the OOo stuff from the website instead of the repo.  Seeing that the repo has caught up with what I am running I am installing it now.

I need to go and check my other installs anyway so I will see what happens when I reboot.  It tells me in need to log back in so I may as well wait until I go running around the test platform to see what broke where and if my minimal install (9.10 mini upgraded to 10.04 running Gnome Desktop) is working again.

I will report back then.

---

### Post by seeker5528 on 2010-02-27
> **ranch hand said:**
> seeker5528
This is all your fault and I hope it works out.

LOL!!!

> I did check the Language Support deal and it claimed I didn't have it fully installed.  This is due to using the OOo stuff from the website instead of the repo.  Seeing that the repo has caught up with what I am running I am installing it now.

It complains to me about language support not being fully installed as well, I always choose the option to remind me later. I think in my case it is only because I installed some extra stuff in an attempt to get all the characters in the file names/tags of my music files to show up, the details show the stuff that is not installed is either not english or is non-US english.

 Some of the Polish and Russian files still have some characters that show as a box instead of a letter, GRRR!!! Interestingly, when these get scrobbled to Last FM and I look at the recently played songs or if I am making a post in a forum and copy and past the name into my post, Firefox displays all the characters correctly. :confused:

Later, Seeker

---

### Post by VMC on 2010-02-27
I'm sure its not set for me as well, because when I install Ubuntu, I turn off the internet when it tries to get online and download the language files. Thinking I don't need them. Usually I don't, but in this case, apparently I do. Or at lease to be able to set the language.

---

### Post by ranch hand on 2010-02-27
What ever the case may be, now that I am back the order is restored.

Of course I couldn't open any OOo stuff for some reason but I removed it all and reinstalled it and now it works again.  When I removed it the language support was removed and not reinstalled.  I found it and got it too so I am probably good even tomorrow when I boot back in.

---

### Post by lidex on 2010-02-27
> Sort order is controlled by LC_COLLATE. Sort orders can differ within the same writing system. In ASCII order, the upper-case letters as a group precede the lower-case letters: A B C ... a b c.... In French, upper-case letters immediately follow their lower-case counterparts: a A b B c C.... In some other locales upper-case letters immediately precede their lower-case counterparts: A a B b C c....

Sort order affects not only sorting but character ranges in regular expressions. In ASCII order, the range expression [A-Z] stands for the 26 upper-case letters. That is because the expression stands for the characters starting with A and ending with Z. In ASCII, the upper-case letters form a contiguous block of 26 running from A to Z. However, in the French locale the letters starting with A and ending with Z consist of all of the letters except for lower-case a.

> Locale variables

There are several locale variables, though some of them have a meaning we haven't figured out yet. :-(

    * LC_CTYPE Character classification and case conversion. Also indicates the language which should be used with XIM.
    * LC_NUMERIC Non-monetary numeric formats.
    * LC_TIME Date and time formats.
    * LC_COLLATE Collation order used for comparing and sorting.
    * LC_MONETARY Monetary formats.
    * LC_MESSAGES Formats of informative and diagnostic messages and interactive responses (also for graphical user interfaces).
    * LC_PAPER Paper format.
    * LC_NAME
    * LC_ADDRESS
    * LC_TELEPHONE
    * LC_MEASUREMENT
    * LC_IDENTIFICATION 

(We don't know what exactly the last 5 variables are for ...)

Special variables.

There are two variables that affect all of the above one, and it is important to understand the difference between them.

    * LANG: Its value is used to set the value of all LC_* variables which are not explicitely set (those already set are not changed). Also, any LC_* variable can be modified after setting LANG.
    * LC_ALL: Its value will override all the LC_* variable (but not LANG). After setting LC_ALL, modifications to any LC_* variables are not permitted.
    * In general, it is then recommended to leave LC_ALL unset, set instead LANG, and change individual LC_* variables to suit your needs. 

How to check and modify the value of locale variables

    * The simplest way is to type locale in your shell.
    * Those variables whose values are within quotation marks are those which are not set explicitely, and inherit their values from LANG or LC_ALL. Those values without quotation marks have been set explicitely.
    * To set or modify a locale variable, use the setenv command, for instance:
      setenv LANG es_ES
    * A list of all available locales can be obtained by typing:
      locale -a
    * To change permanently your locale to (american) english, you may place in your .cshrc file the instructions:
      setenv LANG en_US
      setenv LC_ALL en_US 

[COLOR="Navy"]*What I've taken from all this is the LC_COLLATE value should govern the sort order as long as LC_ALL is unset. If LC_ALL has a value, then LC_COLLATE inherits that value. The output of "locale -a" shows the locales available on your system. So if you have a value of "C", changing it to POSIX or the appropriate UTF-8 will either fix it or I am completely wrong.*[/COLOR]

---

### Post by ranch hand on 2010-02-28
I would say that, from what I did, you are right.  This has obviously changed however as I am back on 9.04 for the night and it is set a C and it sorts the lowercase first and then the upper case of the same letter second,  This is what is happening, again, in 10.04.

Up untill about a week ago 10.04 was working the same as the version in 9.04 and 9.10.

Real interesting.  And educational too.

---

### Post by kansasnoob on 2010-02-28
I'll be darned! It was that simple :D

Works great now, thanks.

---

### Post by kansasnoob on 2010-02-28
I am curious about something though, what are these keyboard input options:

[ATTACH]148494[/ATTACH]

I just never messed with that before.

---

### Post by lidex on 2010-02-28
> **ranch hand said:**
> I would say that, from what I did, you are right.  This has obviously changed however as I am back on 9.04 for the night and it is set a C and it sorts the lowercase first and then the upper case of the same letter second,  This is what is happening, again, in 10.04.

Up untill about a week ago 10.04 was working the same as the version in 9.04 and 9.10.

Real interesting.  And educational too.

So then the "C" value sets it to ASCII order, it looks like.

---

### Post by ranch hand on 2010-02-28
Yup, sure does.

---

### Post by ranch hand on 2010-02-28
> **kansasnoob said:**
> I am curious about something though, what are these keyboard input options:

[ATTACH]148494[/ATTACH]

I just never messed with that before.
The smartass answer is "man nautilus is your friend".  Unfortunately that is the only one I have for you.

I intend to look at that just as soon as I get back to 10.04 in the morning.  I never saw the like of that before.

I think they put that stuff on just to torture us older folks.  Kind of a "let's see if we can teach old dogs new tricks".  All I can say is that I sure hope age an treachery comes through for us again.

---

### Post by mdurham on 2010-02-28
I had this problem. I think you can set the correct Local in the login screen.

---

### Post by sonicb00m on 2010-02-28
> **ranch hand said:**
> I have not done this completely yet.  found the line that needs editing but have not tryied the recompiling yet as there are a couple  of things I do not understand quite.

If you had searched for a nautilus thread in this forum you would have found this;

[http://ubuntuforums.org/showpost.php?p=8865200&postcount=84](http://ubuntuforums.org/showpost.php?p=8865200&postcount=84)

which should get the tabs back where they belong.

If I have success with that I may go hunting for the part that does the sorting of files.

That worked perfectly! Thanks.

---

### Post by ranch hand on 2010-02-28
Geeze, that is almost a bummer.  It failed for me.

---

### Post by sonicb00m on 2010-02-28
> **ranch hand said:**
> Geeze, that is almost a bummer.  It failed for me.

My first mistake was to comment out the code with # then it wouldn't compile. Then i remember it was C and not php :p

---

