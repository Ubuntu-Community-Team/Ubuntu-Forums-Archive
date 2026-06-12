---
title: "a complete/secure delete program?"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by truenemesis on 2006-06-27
are there any programs on linux that will perform a complete wipeout of the harddrive? As in unrecoverable rm command. I have some sensitive data that I transferred already. I dont want any remaining fragments.

---

### Post by Dr. Nick on 2006-06-27
Hmm not sure exctly, Are you trying to wipe an entire drive?

I think its pretty secure to rm it all, then delete all the partitions and make a one large partition and format it in a different filesystem, then delete that partition and make another and format it in a different filesystem. 

Their are also several boot cds that can be used to destroy data.

If you are just trying to "wipe free space" on a drive I am not sure

---

### Post by truenemesis on 2006-06-27
well, I want to be able to delete files and folders to the extent that they cant be restored or recovered. I had password files and all deleted. Just dont want them to be restorable.

---

### Post by polka on 2006-06-28
You are right silply doing a rm and overwriting is not a "secure" delete.
Check out the dd command:
man dd

Something like this should work:

dd if=/dev/zero of=dev/hd? bs=8M
Repeat theprocedure several times (7)

OR

dd if=/dev/urandom of=/dev/hd? bs=8M
Repeat several times depending on the level of your paranois.

THis one is slower but supposedly "more secure"
HTH
Jerry

---

### Post by jonmack on 2006-07-02
Try the "shred" command. It will wipe over a given file, with loads of options (see "man shred") for number of random passes, finish with 0's, delete after shred etc.

---

### Post by Dr. Nick on 2006-07-02
[quote=jonmack]Try the "shred" command. It will wipe over a given file, with loads of options (see "man shred") for number of random passes, finish with 0's, delete after shred etc.[/quote]

Wow! glad you chimmed in with that, Its one of them things you think they would have already included, but a quick search of forums and the internet fail to reveal it. This is the first mention of "shred" I have seen. 

Welcome to the Forums

---

### Post by John.Michael.Kane on 2006-07-02
Heres more info on [**[COLOR="Red"]shred[/COLOR]**]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=s/shred") also if your doing whole disk wipes you may want to look into [**[COLOR="SandyBrown"]dban[/COLOR]**]("http://dban.sourceforge.net/")

---

### Post by rcarring on 2006-07-02
The most secure way to erase a disk is to do a low level format using the utility that the hard disk manufacturer provides.

I have also found that overwriting the file you wish destroyed with one of the same name is foolproof -- I checked it once using a disk file recover tool and all it could find was the file I used to overwrite, not the original file.

---

### Post by Dr. Nick on 2006-07-02
Yeah a low level format is a good idea too, That is a good thing to do if you are giving the hard drive to someone else, or throwing it out. A low level format is alot better than a regular format. 

I never thought about making a file with the same name, pretty clever idea

---

### Post by ryu kun on 2006-11-11
Well, I'd like to mention here from "[Eraser]("http://www.heidi.ie/eraser/")" which is an open-source windows tool to shred files. Just in case somebody might need it some time, like me.

---

### Post by itchanddino on 2006-11-11
Whenever I needed to wipe a hard drive, I use the live CD distro [SystemRescueCD]("http://www.sysresccd.org/Main_Page").  Very handy and it comes with shred.

---

### Post by temp2264 on 2006-11-12
just googled a bit maybe is this it 

[http://www.jetico.com/index.htm#/bcwipe_unix.htm](http://www.jetico.com/index.htm#/bcwipe_unix.htm)
or [http://wipe.sourceforge.net/](http://wipe.sourceforge.net/)
or [http://jeenyus.net/~budney/linux/software/fwipe.html](http://jeenyus.net/~budney/linux/software/fwipe.html)
or [http://abaababa.ouvaton.org/wipe/](http://abaababa.ouvaton.org/wipe/)

---

### Post by yme on 2007-05-19
I'm very surprised nobody has mentioned Darik's Boot & Nuke yet. If you want to be sure you have a shinny clean HD it is by far the best choice:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It has a number of options for wiping, including the Gutmann method, which I understand to be the most secure:
[http://en.wikipedia.org/wiki/Gutmann_method](http://en.wikipedia.org/wiki/Gutmann_method)

yme

---

### Post by HumbleGod on 2007-05-19
> **yme said:**
> I'm very surprised nobody has mentioned Darik's Boot & Nuke yet.

Sure they did....see SD-Plissken's comment on July 2nd, 2006. :)

---

### Post by altonbr on 2007-05-23
Guys, guys, guys: Enable universe and multiverse and run this:

```
sudo aptitude install secure-delete
```

Now you should have the binaries for 'srm', 'sfill', 'sswap' and 'smem'. 'srm' is the secure version of 'rm' of course.

---

### Post by gnyffel on 2007-10-16
Seeing as this thread is likely to turn up in search results, I just thought I'd mention that NO ONE can recover data from a drive that's been given a single wipe with /dev/null. Anything beyond that is a waste of time.

---

### Post by az on 2007-10-16
> **gnyffel said:**
> Seeing as this thread is likely to turn up in search results, I just thought I'd mention that NO ONE can recover data from a drive that's been given a single wipe with /dev/null. Anything beyond that is a waste of time.

Not true.  I do this professionally.  


To ensure that your data is safe, your best bet is a drill.

---

### Post by altonbr on 2007-10-17
Or a smelter ;)

---

### Post by Palmyra on 2007-11-02
> **az said:**
> Not true.  I do this professionally.  


To ensure that your data is safe, your best bet is a drill.


Sure, but even then you have to ask: how much drilling is enough?  How long must a hard drive be in hell fire before all data is fully wiped?  You can go on and on with these hypotheticals.

Using DBAN is a true and tried method.  If you know of ANY instances in which data wiped by DBAN was recovered, please let me know.  The developers of DBAN will not make any guarantees, but they are just being humble.  High level government agencies use DBAN (which, more than any of us, have something to hide!).

Give it a try.  DBAN is rock-solid, and it has a proven track record.

---

