---
title: "Broken Package"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by mathisonej on 2010-04-26
Hello,

I upgraded to 10.04 from 08.04 a little while ago, and everything worked fine except I'm now getting a "Broken Package" message on my package manager regarding the "flashplugin-nonfree" package. I've seen some other posts about this but I can't get it fixed: when I search for 'broken' in synaptic package manager under filters nothing shows up, and I can't delete or update the flash package.

If this has been solved elsewhere or anyone can help me otherwise I'll be grateful.

Eric

---

### Post by zvacet on 2010-04-26
In synaptic>edit tab>fix broken packages

or from terminal

```
sudo apt-get -f install
```

---

### Post by mathisonej on 2010-04-26
Thanks Zvacet.

When I go to fix it in synaptic it says that I need to reinstall it because the package is in a bad inconsistent state. But when I try to install it in synaptic it says the same thing. Is there another way to reinstall it?

Eric

---

### Post by cuberts on 2010-04-26
[PHP]sudo apt-get <package>[/PHP]

---

### Post by mathisonej on 2010-04-26
When I run[PHP]sudo apt-get flashplugin-nonfree[/PHP] it tells me that it is an invalid operation. If I run [PHP]sudo apt-get -f install[/PHP] I get this message: [PHP]Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

I'm not really sure how to proceed. Thanks again to those trying to help me out.

Eric

---

### Post by slickh20 on 2010-04-26
I have this same problem exactly.  

it is keeping me from updating any thing beyond this,  I also cant remove the package either.

---

### Post by QIII on 2010-04-27
You might try

```
sudo apt-get install --reinstall <package>
```and let us know what happens.

Did you ever get a message something like "you must manually run 'sudo dpkg --configure -a' to correct the problem"?

---

### Post by mathisonej on 2010-04-27
QIII,

When I run that I get this message:[PHP]eric@eric-laptop:~$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/PHP]

Then when I run the install I get the same result as before.

Eric

---

### Post by QIII on 2010-04-27
Try 

```
sudo apt-get install flashplugin-installer flashplugin-nonfree
``` 

The message you are getting indicates that the dependency flashplugin-installer is absent.

---

### Post by mathisonej on 2010-04-27
I'm afraid I'm getting the same message: [PHP]dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

---

### Post by QIII on 2010-04-27
OK.

Could you go to Synaptic and tell me if flashplugin-installer is now listed as installed?

---

### Post by mathisonej on 2010-04-27
It isn't installed, but marks itself for installation. If I try to install it I get the message about the other one being broken.

---

### Post by QIII on 2010-04-27
Grrr.

OK.  Back to the terminal.  Let's see if dpkg got interrupted somewhere.

```
sudo dpkg --configure -a
```

If that doesn't work, I'll have to do a bit of research for you.

---

### Post by mathisonej on 2010-04-27
I'm not getting anything substantial out of that. This is it: [PHP]eric@eric-laptop:~$ sudo dpkg --configure -a
eric@eric-laptop:~$[/PHP]

Thanks for helping me this far!

---

### Post by slickh20 on 2010-04-27
following along exactly the same here, same results....  thanks

---

### Post by QIII on 2010-04-27
You might not see any results.

(Sorry this is taking so long.)

Go back to Synaptic and see if you can install both libflashplayer-installer and libflashplayer-nonfree.

---

### Post by mathisonej on 2010-04-27
I can't find either of those when I search in synaptic. I tried to install the flashplugin-nonfree and flashplugin-installer again (just to check) and it didn't work.

If I have missed something simple, forgive me.

---

### Post by QIII on 2010-04-27
Ah.  Remove the "lib" from in front of each of those.  Sorry.  It's late here.

---

### Post by QIII on 2010-04-27
Could you see if you have this file?

/var/lib/dpkg/info/flashplugin-nonfree.prerm


I think I found something on launchpad, but it is for Karmic.  It may work for Lucid.  But I don't want to direct you there unless you have that file.

---

### Post by mathisonej on 2010-04-27
I still can't find the two flash files, even without the 'lib' prefix. Regarding the other one: I'm not sure if I'm going about this the right way. When I use 'find' in the terminal it repeats the search: [PHP]eric@eric-laptop:~$ find /var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.prerm[/PHP]

If I search under places nothing shows up. Is that the right way to check for the file?

---

### Post by QIII on 2010-04-27
Bah.  REALLY late.  Yes.   flashplugin-nonfree and flashplugin-installer.

The command in the terminal said it found it.  In nautilus, it may take a while to populate the list.  How long did you wait?

PS:  You could also use

```
locate flashplugin-nonfree.prerm
```

to see if it is in that directory.
[COLOR=#000000][COLOR=#0000BB] [/COLOR][/COLOR]

---

### Post by QIII on 2010-04-27
I have to get to bed.

I think you have the file, so I am going to direct you here:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)

Look at post #8.  Again, this is Karmic, not Lucid.

I would recommend using cp before the rm (if you copy, you can always get something back.)

So maybe do this first:

```
sudo cp /var/lib/dpkg/info/flashplugin-nonfree.prerm /var/lib/dpkg/info/flashplugin-nonfree.prerm_BAK
```Then follow the rest.

---

### Post by mathisonej on 2010-04-27
Okay. It seems that I have it: [PHP]eric@eric-laptop:~$ locate flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.prerm[/PHP]

For the synaptic files I tried to install them and it repeated the same message, but when I open up 'details' it says [PHP]A package failed to install. Trying to recover:[/PHP]

And it has been thinking for a while on that. I'll leave it for a bit and see what happens. I need to pack it in for the night (and you should too!), but if you want to leave the instructions for the Karmic thing I can try that, and post my results tomorrow. If you don't want to, we can pick it up later!

Thanks again.

---

### Post by slickh20 on 2010-04-27
yes thank you very much

---

### Post by slickh20 on 2010-04-27
I think that did it!!! 

be sure to put sudo in front of those three commands in post number 8

---

### Post by QIII on 2010-04-27
slickh20 --

Glad to hear that worked for you.  I was looking for something like that  while I was trying a more conservative approach.

We'll see if that helps mathesonej.

mathesonej --

If this works for you, would you please mark your original solved?  Also, this might be a regression bug that the developers need to know about.  It might be important for you to report this as a bug in Lucid.

---

### Post by mathisonej on 2010-04-28
Solved! Thanks so much.

---

