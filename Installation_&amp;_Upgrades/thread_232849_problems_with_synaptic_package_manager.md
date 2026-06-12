---
title: "problems with synaptic package manager"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by toosweetnitemare on 2006-08-09
E: The package jedit needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


this is error ive been getting. it started after i downloaded jedit and i deleted, now i can not get rid of this message, but the worst part is i can not upgrade nor add/remove apps either. any ideas on how to just get rid of jedit in its entirety so i can go one with life haha

---

### Post by bscbrit on 2006-08-09
It might be that you have corrupted your repository data.  Try

sudo apt-get reload

and make sure that you see no errors there.

---

### Post by toosweetnitemare on 2006-08-09
E: Invalid operation reload


thats what is happening when i try the sudo apt-get reload command

---

### Post by bscbrit on 2006-08-09
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Make sure that you have a valid set of repos in /etc/apt/sources.list   Save your current list as sources.list.orig if you are going to make any changes to it.

sudo apt-get update

Hope that the errors go away, otherwise you will have to clear out the cache and recover apt-get that way.  Not difficult but a pain.

---

### Post by toosweetnitemare on 2006-08-09
master@master-laptop:~$ cd /etc/apt/sources.list
bash: cd: /etc/apt/sources.list: Not a directory
master@master-laptop:~$ cd /etc/apt/sources.list.d/
[email]master@master-laptop:/etc/apt/sources.list[/email].d$ ls
dapper-multiverse.list       dapper-universe.list
dapper-multiverse.list.save  dapper-universe.list.save


this is what i have. how should i run an update to just refresh them? because i ran the sudo apt-get update and it updated but im still getting 

E: The package jedit needs to be reinstalled, but I can't find an archive for it.

---

### Post by henrikca on 2006-08-09
I've got exactly the same problem and my sources.list seems intact.
apt-get update seems to run without problems, but Synaptic is still broken.
Please help ;)

---

### Post by drlock on 2006-08-09
How did you guys install JEdit?  It has its own debian repository, did you use that?

I would try and make sure the Jedit Repository is setup in your sources.list file.  Then apt-get will be able to find the package and might clear itself up.  Have a look here for details: [http://www.cs.cornell.edu/~djm/ubuntu/#jedit](http://www.cs.cornell.edu/~djm/ubuntu/#jedit)

---

### Post by bscbrit on 2006-08-09
toosweetnitemare

you should have checked the file '/etc/apt/sources.list/' to make sure that its contents are similar to the repos that I posted in the link.  Don't bother going into the sources.list.d directories.

Once you are happy that the file contents are not corrupted and that they only point to valid repos, run the following command:

sudo apt-get update
sudo apt-get check
sudo apt-get remove jedit


The package 'jedit' does not exist in any of the repos that I can find.  I don't know where you downloaded from but you can't update it so we will try to remove it.  Note the output of the commands but they might give us a clue on where the problem is.  If there are any messages, please post them in full in your next reply.

[EDIT] the previous post might be useful if you want to include it in your repos. Drlock has found the repos.

---

### Post by henrikca on 2006-08-09
I've tried that. But the following "sudo apt-get install jedit" reports the same: "E: The package jedit needs to be reinstalled, but I can't find an archive for it."

---

### Post by henrikca on 2006-08-09
Hi' bscbrit,
I've done that, but both the "check" and "remove" give the same error

---

### Post by bscbrit on 2006-08-09
Did you include the repos suggested by Drlock which is where, presumably, you downloaded jedit from in the first instance?

---

### Post by henrikca on 2006-08-09
Yes, I did add the mentioned repos
[edit] Sorry, never told, that Synaptic also says: "E: Internal error opening cache (1). Please report."

---

### Post by drlock on 2006-08-09
I am not sure about the cache error.  But if it is just getting stuck on removing jedit you may be able to work around with dpkg. Try:
```
dpkg -l jedit
```
and see what the Desired/Status/Error values are.

You can tell dpkg to remove jedit with:
```
sudo dpkg -r jedit
```
or (to get all pending removals)
```
sudo dpkg -r --pending
```

That might clear it up enough to run the other commands bscbrit suggested

---

### Post by toosweetnitemare on 2006-08-09
yes i have done the same steps and i am still getting the errors. ill keep trying and post with my finds

i went to  sudo gedit /etc/apt/sources.list


and deleted 

deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./

now i am getting 
 

dpkg: conflicting actions --field and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@master-laptop:/home/master# sudo dpkg -r --pending
dpkg: error processing jedit (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 jedit

---

### Post by henrikca on 2006-08-09
Trying this:  sudo dpkg -r jedit
With this result:

dpkg: error processing jedit (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 jedit

Seems like I'm stuck:(

---

### Post by toosweetnitemare on 2006-08-09
henrikca, im in the same boat, how did you install the jedit and delete it? i think we had to do something similar because we both have all the same errors. maybe we can reverse work the issue to the source.

---

### Post by henrikca on 2006-08-09
I installed it from the Debian package on the Jedit download page. I never mange to delet it. Look in the thread to see what I've tried to do. 
- I'm pretty close to consider an Ubuntu reinstall.

---

### Post by toosweetnitemare on 2006-08-09
ya i hear ya but ive custumized it soo much im too lazy to do it all over again. have you tried a 

find / -name "jedit"

command because thats what i did to delete everything. i cant find anything marked jedit on my system. can we do a roll back to before installing jedit?

---

### Post by henrikca on 2006-08-09
Tried: find / -name "jedit"
Nothing to find

---

### Post by toosweetnitemare on 2006-08-09
well then i am at a loss of what to do. maybe we should wait to see if anyone else has an idea, i mean i cant even reinstall it or delete the remains, that is messed up

---

### Post by henrikca on 2006-08-09
I'm out of ideas as well. Hope a real pro comes around with some help.

---

### Post by bscbrit on 2006-08-09
OK, lets try to find where the file is referenced.  You've searched for the file itself now look for references

sudo grep /etc/apt -R jedit 

and see which files it throws up.  Then we can look at editing those files to remove the references to jedit to try and get Synaptic working again.

---

### Post by henrikca on 2006-08-09
sudo grep /etc/apt -R jedit 
No result.

---

### Post by toosweetnitemare on 2006-08-09
yep same here that didnt pull anything up.

---

### Post by bscbrit on 2006-08-09
Was the program name jedit or Jedit?  You might want to try searching the /var/cache/apt/ directory also.  Try looking at 'man grep' to see if there is a better match.  

I'm supposed to be packing up my home prior to moving and my other half thinks I'm spending too much time on the computer - she's probably right, too!  But I'll keep popping back to see how things are going.  If I have any particularly bright ideas I'll let you know!

---

### Post by henrikca on 2006-08-09
Hi' bscbrit,
No result, no matter how I do the search

---

### Post by bscbrit on 2006-08-09
That should be

grep -R /etc/apt/* jedit

and

grep -R /var/cache/* jedit

My mistake - its late and I'm tired.

---

### Post by henrikca on 2006-08-09
Still no result. My bed is calling. Will be back to morrow.

---

### Post by bscbrit on 2006-08-10
> **henrikca said:**
> Still no result. My bed is calling. Will be back to morrow.

The problem probably lies in the /var/cache/apt/ directory somewhere.  Search using ls in that directory and see if you can find any files that seem to be related to 'jedit'.  Remove them if you can.

If that doesn't help, I would be tempted to delete everything below /var/cache/apt and rebuild the repositories from scratch.  I've never done this but it still seems worth a try before being forced to re-install Ubuntu from scratch again.  After all, when you first install Ubuntu, the cache must be empty and it will presumably re-initiate itself during the first read of the repository list.

Can you post the contents of /etc/apt/sources.list for me to look at please?

---

### Post by henrikca on 2006-08-10
Hi'
I'm away from my beloved Ubuntu until late this afternoon - I'll collect the info for you when I return.

---

### Post by toosweetnitemare on 2006-08-10
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main



##jedit
deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./








that is everything from the gedit /etc/apt/sources.list
 commmand


ive also tried sudo apt-get remove --purge jedit

master@master-laptop:~$ sudo apt-get remove --purge jedit
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.

---

### Post by toosweetnitemare on 2006-08-10
i figured it out!!!!!!!!!!!!!



sudo dpkg --remove --force-depends --force-remove-reinstreq jedit



if worked and now my package manager loads, i about to go and check the rest out.

---

### Post by henrikca on 2006-08-10
Thank you toosweetnitemare!

You saved my day. It's a pleasure to have got all these Ubuntu friends.
- and thank you  **bscbrit** for your perssitant efforts.

:KS Henrik

---

### Post by toosweetnitemare on 2006-08-10
you are welcome henrikca, and thank you again bscbrit

---

### Post by bscbrit on 2006-08-10
Great news - and you solved it yourself!  I'm making notes of this for next time someone has a similar problem.

No thanks necessary - return the favour to someone else on the forum in the future.

---

### Post by jfreax on 2006-08-24
> $ LANG=en_US sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 360567 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit

:(

---

### Post by mlie on 2006-08-26
Thanks a lot!!!! It happens to me too... All the same process..  Many many thanks... :) :) No more jedit!!! :P

---

### Post by mikedpt on 2006-08-26
Thank you toosweetnitemare.  I ran into this problem this same problem when I tried to install jedit.

---

### Post by zimmermann on 2006-08-27
Same problem with jedit package, and I get the same error messages as jfreax when running:
sudo dpkg --remove --force-depends --force-remove-reinstreq jedit

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 82630 files and directories currently installed.)
Removing jedit ...
dpkg (subprocess): unable to execute post-removal script: No such file or directory
dpkg: error processing jedit (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit


Can anyone help? Things are pretty broken here. :confused:

---

### Post by Maxximillian on 2006-08-28
I keep having a similar problem. Anytime I go to download something via synaptics, I get this:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured

---

### Post by nicstevens42 on 2006-09-04
I, too, have been bitten by the install of jedit. 

Here's something that bothers me tho... 

It is wholly reasonable to expect that a broken, damaged, or otherwise messed up package might be downloaded and installed via apt-get. How can apt get allow the package database to get so corrupted without the ability to roll-back on install failure? 

That's pretty much a no-brainer from a design perspective. 

ubuntu is supposed to be linux for everyone and I have been developing software and using unix/linux for many years and navigating the corruption and rebuilding of the apt/dpkg databases is a mystery to me... 

Is a noob user going to know how this works or will he get frustrated and run windows xp

---

### Post by w0utje on 2006-11-17
i've been dumb
i wanted to install oss-linux because my sound isn't working
so i downloaded the .deb installation packet.
but on installing he said. you need basic-essentials
so i did it an install it again
but now it was corrupted and so i can do nothing with synaptic
even the "final" command doesn't work for me.. ](*,) 
finally i've have ubuntu 6.10 dual boot on my laptop
wifi is working...
and now this.. HELP!?!?!

---

### Post by mwp007 on 2007-01-06
remove all files beginning with your package name from /var/lib/dpkg/info/ and the try again.
i've  had this f.... problem with pipsplus package.

---

### Post by jisaac on 2007-01-13
Thanks mwp007.

I solved a similar problem I had with another package removing all the files has you said...

---

### Post by hantms on 2007-01-27
I'm having a simimlar problem, but with a different package.

All the solutions so far don't work, apt-get remains broken so I can't install or uninstall anything.

This is what happens:

dpkg --remove --force-remove-reinstreq virtualbox

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 109242 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--remove):
 subprocess pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox

----------

And that's it.  Without the --force-remove-reinstreq option it also doesn't work. 

Any clues?  I don't want to reinstall the whole of Ubuntu again if at all possible.

---

### Post by Zkupa on 2007-01-30
I had the same problem as you hantms. 
Had googled around the last 2 days trying to find a solution, I found this thread: [http://www.ubuntuforums.org/showthread.php?t=344124]("http://www.ubuntuforums.org/showthread.php?t=344124")

Suggestening to go here: [http://www.virtualbox.org/wiki/User_FAQ]("http://www.virtualbox.org/wiki/User_FAQ")

So i did that.. and my synaptic / apt-get is up and running !

---

### Post by .tommie on 2007-02-03
I've had a similar issue with Skype. Solved it with the command posted by toosweetnitemare... thanks!

> user@notebook:~$ **sudo dpkg --remove --force-depends --force-remove-reinstreq skype**
dpkg - waarschuwing, probleem wordt geforceerd omdat --force aanstaat:
 Pakket is in een ernstige inconsistente status - u moet het opnieuw
 installeren alvorens het te verwijderen.
(Database inlezen ... 
dpkg: ernstige waarschuwing: bestandenlijst-bestand voor pakket
`skype' ontbreekt, aangenomen wordt dat het pakket geen bestanden
heeft geïnstalleerd.
114139 bestanden en mappen geïnstalleerd.)
skype wordt verwijderd ...

---

### Post by thegitksan on 2007-06-30
I am encountering exactly the same problem. Tried installing a generic winmodem driver, the install failed and now i am stuck with almost exactly the same message and the same loop. Only the name of the app is different, but the error message is exactly the same and the behaviour is the same too.

Still looking for answers.

Russ

---

### Post by thegitksan on 2007-06-30
> **toosweetnitemare said:**
> i figured it out!!!!!!!!!!!!!



sudo dpkg --remove --force-depends --force-remove-reinstreq jedit



if worked and now my package manager loads, i about to go and check the rest out.
-------------------
Just tried this myself and it replies with exactly the same message, "E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: internal error opening cache(1). Please report."

And that's the same message I have been staring at for 2 days with no solution yet in sight.

Is there a Synaptics trouble-shooting thread here I can work my way through?

The processing messages, BTW, looked almost identical to those following this thread a bit later on, lots of "Can't find this, That's already in use by some totally other prog".

Well, where else should I look? I am not yet finding an answer to my loss of Synaptic to this failed installation.

---

### Post by boogiepop88 on 2007-09-25
i love this thread, thanks to all your hard work guys.


this happened to me with virtualbox instead of jedit

---

