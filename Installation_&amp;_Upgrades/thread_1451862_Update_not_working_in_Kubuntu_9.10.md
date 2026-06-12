---
title: "Update not working in Kubuntu 9.10"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Ederico on 2010-04-11
I don't what it is called exactly, but the update application is not working. I'm getting the same error all the time and cannot update my system. I'm running Kubuntu 9.10 at the moment. Here is the code I get when I click on details for the error message:

```
Error Type: 
Error Value: installArchives() failed
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1952, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1949, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1911, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 647, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 611, in dispatch_command
self.update_packages(package_ids)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 168, in _unlock_cache_afterwards
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1099, in update_packages
if not self._commit_changes(): return False
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1624, in _commit_changes
PackageKitInstallProgress(self, install_range))
File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 318, in commit
raise SystemError("installArchives() failed")

```

I hope someone can help, thanks beforehand.

Ederico.

---

### Post by jamiepedder on 2010-04-17
Hi there!  

Not sure if its related, but heres how I got round a very similar error message to yours - I must point out I'm using Lucid but I'm sure if its a similar issue it would effect you in the same way.

Because KPackagekit kept bumming out with that error message, I decided to try 'sudo apt-get upgrade' at a konsole prompt.

This errored out too, but gave me some clue as to what was happening.  It said something about 'unknown group in statoverride file'.  I located the file at /var/lib/dpkg/statoverride and opened it - inside was a line referring to a program called gnokki which I had uninstalled much earlier.  After deleting that line, both kpackagekit and 'sudo apt-get upgrade' started working again with no errors.

So my advice - check the statoverride file - but try the apt-get upgrade command first and see if that gives you an error you can understand.

Hope this helps!

---

### Post by Ederico on 2010-04-30
I did sudo apt-get upgrade and I got this error message:

```
dpkg: apertura del file di informazioni sui pacchetti "/var/lib/dpkg/available" in lettura non riuscita: Nessun file o directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

The error message in Italian translates to something like opening of information file "/var/lib/dpkg/available" to read unsuccessful: No file or directory

I tried upgrading to 10.04 LTS right now, and it didn't work either, basically I cannot do any updating/upgrading.

---

### Post by ShagzModo on 2010-05-19
same error here I am running 10.04 i386.
No idea how to fix it; tried this so far!

unrecoverable fatal error, aborting:
syntax error: unknown group 'gnokii' in statoverride file


paul@d630:~$ sudo groupadd gnokii
[sudo] password for paul: 
paul@d630:~$ sudo dpkg -P gnokii-cli
(Reading database ... 198194 files and directories currently installed.)
Removing gnokii-cli ...
Purging configuration files for gnokii-cli ...
gnokii:x:1002:
dpkg-statoverrides: unrecoverable fatal error, aborting:
syntax error: unknown group 'gnokii' in statoverride file
paul@d630:~$ sudo dpkg-statoverride --remove /usr/sbin/mgnokiidev
dpkg-statoverrides: unrecoverable fatal error, aborting:
syntax error: unknown group 'gnokii' in statoverride file
paul@d630:~$  groupdel gnokii
groupdel: group 'gnokii' does not exist
paul@d630:~$ sudo dpkg-statoverride --remove /usr/sbin/mgnokiidev
dpkg-statoverrides: unrecoverable fatal error, aborting:
syntax error: unknown group 'gnokii' in statoverride file
paul@d630:~$ ^C
paul@d630:~$

---

### Post by krtica on 2010-05-29
This is what I have done, and it helped me:

I opened file:

```
sudo gedit /var/lib/dpkg/statoverride
```

and delete part I recognized from from warning:

```
root gnokii 4750 /usr/sbin/mgnokiidev
```

After that I could install/uninstal/upgrade again.

I'm not sure is it right thing to do, but it helped me.

---

### Post by ShagzModo on 2010-05-30
root gnokii 4750 /usr/sbin/mgnokiidev could not be found first time i assessed the situation...
override file was empty

 decided to overhaul install completely with fresh 10.04 i386 install on laptop. de cluttered 3 years of docs, backed up important stuff to external drive and synced important stuff with ubuntu one...

Been upgrading upto 10.04
happy with uncluttered sys...

---

### Post by ojmc on 2010-06-04
I had the problem too when updating, "syntax error: unknown group 'gnokii'" etc.

I tried krtica's solution and "delete part I recognized from from warning" and now have a new error.

[COLOR=DarkSlateGray]Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 statoverride file contains empty line
E: Sub-process /user/bin/dpkg returned an error code (2)
A package failed o install.   trying to recover:[/COLOR]

I didn't use the command line as krtica did.
I just went to the file /var/lib/dpkg/[COLOR=DarkSlateGray][COLOR=Black]statoverride in Nautilus and deleted the line that contained mgnokiidev in it.

I can't  update anything now.

I'm[/COLOR][/COLOR] not big on command line stuff but will give anything a go. 

Anyone have an idea how to fix this mess?

Thanks

---

### Post by krtica on 2010-06-05
"*statoverride file contains empty line*"

I was told once that empty line at the end of this file can result in lots of troubles.

---

### Post by ojmc on 2010-06-05
But do you have any idea what to do krtica. 

Do you know why this second error has happened to me and not to you?

And most important, would you by any chance have backed up this line, as I did not and do not recall what was in it so I cannot now replace it?

Many thanks

---

### Post by krtica on 2010-06-05
I think it was:

root gnokii 4750 /usr/sbin/mgnokiidev

But, you should check first do you maybe have empty lines in /var/lib/dpkg/statoverride file.

---

### Post by ojmc on 2010-06-05
Hi krtica, many, many thanks.

I thought i was going to have to do a clean install.
Anyway, I feel a bit foolish about the empty line thing.
Everything upgrading and working perfect again.
Very grateful, thank you.

---

### Post by krtica on 2010-06-05
You are welcome, ojmc.
I'm happy I finally could help someone. :D

---

### Post by Ghostless on 2010-06-07
I had the same message after messing with gnokii... Krtica's fix solved it.

---

### Post by panoet on 2010-06-14
> **krtica said:**
> This is what I have done, and it helped me:

I opened file:

```
sudo gedit /var/lib/dpkg/statoverride
```and delete part I recognized from from warning:

```
root gnokii 4750 /usr/sbin/mgnokiidev
```After that I could install/uninstal/upgrade again.

I'm not sure is it right thing to do, but it helped me.

Its work!!! :popcorn::popcorn:

---

### Post by Vege 4wd on 2010-06-15
Hi, I ran into the same problem as ojmc.
My problem is I do not know how check if the line is empty.
Probably a silly question but any help would be greatly appreciated.

---

### Post by krtica on 2010-06-16
Hi Vege.

Try moving your cursor with arrows keys. If it ends up alone in some line, that means the line exists and it's empty.

---

### Post by Vege 4wd on 2010-06-16
Thanks, yes there was a line that was not really there so I deleted it.
Works fine thanks.:p

---

### Post by ShagzModo on 2010-06-18
stateoverridefile was completely empty...
tried editing with sudo pico

---

### Post by panoet on 2010-06-20
> **ojmc said:**
> I had the problem too when updating, "syntax error: unknown group 'gnokii'" etc.

I tried krtica's solution and "delete part I recognized from from warning" and now have a new error.

[COLOR=DarkSlateGray]Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 statoverride file contains empty line
E: Sub-process /user/bin/dpkg returned an error code (2)
A package failed o install.   trying to recover:[/COLOR]

I didn't use the command line as krtica did.
I just went to the file /var/lib/dpkg/[COLOR=DarkSlateGray][COLOR=Black]statoverride in Nautilus and deleted the line that contained mgnokiidev in it.

I can't  update anything now.

I'm[/COLOR][/COLOR] not big on command line stuff but will give anything a go. 

Anyone have an idea how to fix this mess?

Thanks

I think you've deleted all of stateoveride file. Try put this on your statoveride file :
```
root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip
```

---

