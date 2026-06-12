---
title: "Only choose one package to update from a repository."
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Bramkaandorp on 2012-06-04
I want to use a ppa to update Liferea, but not the other packages in that ppa, since they are more up to date by default.

Is there a way to just "select" one package from a ppa, and keep the standard repository in place for the other packages?

---

### Post by Bramkaandorp on 2012-06-04
Bump

---

### Post by Bramkaandorp on 2012-06-05
Bump

---

### Post by dino99 on 2012-06-05
open up synaptic
reload updates
choose the package you want to upgrade
after installation, deactivate the ppa (synaptic settings repo)
update again

---

### Post by Bramkaandorp on 2012-06-05
> **dino99 said:**
> open up synaptic
reload updates
choose the package you want to upgrade
after installation, deactivate the ppa (synaptic settings repo)
update again

That doesn't do what I want, for as far as I know.

Here's the thing. I want to use the ppa from Christian Kampka ([https://launchpad.net/~kampka/+archive/ppa?field.series_filter=precise](https://launchpad.net/~kampka/+archive/ppa?field.series_filter=precise)), but without using the packages "gtksourceview3" and "lightdm". I want those two to be updated by the standard Ubuntu repository.

Your suggestion would deactivate the entire ppa after updating, which would also deactivate the Liferea package.

If it's not possible to use just one package from a ppa, does anyone know of a good up-to-date ppa exclusively for Liferea? (the one listed on the Liferea homepage is not up to date).

Thanks for the reply, though.

---

### Post by Dave_L on 2012-06-05
You might be able to do this with "pinning".

I can't provide the details, but here are a some references:
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://wiki.debian.org/AptPreferences](http://wiki.debian.org/AptPreferences)
[http://manpages.ubuntu.com/manpages/lucid/en/man5/apt_preferences.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/apt_preferences.5.html)

---

### Post by drs305 on 2012-06-05
I saw this post yesterday, found it interesting, and wanted to see the solution. 

Since a simple solution hasn't been presented for what you want to do, I can offer a convoluted one. The disclaimers are that 1) there must be better solutions, 2) I am not a bash scripter, so the following can certainly be simplified/improved.

The list of the files in the repository are stored in /var/lib/apt/lists/ppa.launchpad.net_kampka_ppa_ubuntu_dists_precise_main_binary-[COLOR="Red"]amd64[/COLOR]_Packages (or [COLOR="Red"]i386[/COLOR]).

The first 3 references are to liferea (liferea, liferea-dbg, liferea-data). 

My thought was to edit the list of the repository's packages to only those 3. I came up with the following command which would do that:
```

head -63 /var/lib/apt/lists/ppa.launchpad.net_kampka_ppa_ubuntu_dists_precise_main_binary-amd64_Packages

```
I tried redirecting that directly back into the same file using 'sudo' but was unable to do so unless I used "sudo -i" . There is a way to do it directly but since the commands I used didn't work, I had to make it a 2-step process. Someone else can figure out a single command, I'm sure.
```

head -63 /var/lib/apt/lists/ppa.launchpad.net_kampka_ppa_ubuntu_dists_precise_main_binary-amd64_Packages-orig > ~/ppa-edited
sudo cp ~/ppa-edited /var/lib/apt/lists/ppa.launchpad.net_kampka_ppa_ubuntu_dists_precise_main_binary-amd64_Packages

```
These commands should produce a ppa listing which includes only the liferea* packages when you run an upgrade command. 

Testing:
[LIST=1]
[*]Run 'sudo apt-get update'.
[*]Use 'sudo apt-get upgrade' and see what files will be upgraded. You will probably see 'lightdm' included in the list. Then select "N" to cancel the upgrade.
[*]Run the commands to edit the ppa's list.
[*]Run 'sudo apt-get upgrade' again. Check to ensure 'lightdm' and others aren't included in the upgrade before pressing "Y". If 'lightdm' is included in the upgrade list, this technique did not work (unless a lightdm upgrade is available from other sources).
[/LIST]

Shortcomings:
1. You would need to do this each time the repository list was run. It wouldn't be hard to create a script to run the 'apt-get update' command, followed by an edit of the ppa list. 
2. As previously stated, this is a pretty rough hack. Undoubtedly there are better ways of doing what you want. It's meant to just throw out something that might lead you to consider other ways of accomplishing what you want.
3. If I was going to do something like this, I would add more steps in the script to keep that ppa disabled and only 'turn' it on at my specific request, since updating the ppa would not be nearly as important as updating my main system files.

Added: Or a much simpler, albeit manual, way:  edit the list before running apt-get update
```
gksu gedit +63 /var/lib/apt/lists/ppa.launchpad.net_kampka_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
```

---

### Post by Bramkaandorp on 2012-06-05
Wow, that's a lot of info.

@drs305: Since it's not a complete solution, I'll wait until something more complete arives. It does sound very interesting, but I don't trust my skills enough to do it.



As an aside:

If a ppa uses an out of date version, will it replace the more up to date version on my computer, or will it only do so when the package on my computer is older?

As an aside to the aside:

Is the "lightdm" package stable?

---

### Post by drs305 on 2012-06-05
APT won't under normal circumstances replace a newer package with an older one; but it would replace an older one from a main repository with a newer one in the ppa, which was your original concern.

*lightdm* causes problems on occasion for some users but is in a LTS release so the devs certainly consider it stable.

---

### Post by Bramkaandorp on 2012-06-05
> **drs305 said:**
> APT won't under normal circumstances replace a newer package with an older one; but it would replace an older one from a main repository with a newer one in the ppa, which was your original concern.

*lightdm* causes problems on occasion for some users but is in a LTS release so the devs certainly consider it stable.

Well, the version in the main repository is more up to date than the one in the third party (this is the "gtksourceview3" package), so would that mean that the main repository won't be overruled?

And the lightdm in the third party ppa is more up to date than the main one, so I don't know if that one is stable.

---

### Post by drs305 on 2012-06-05
> **Bramkaandorp said:**
> Well, the version in the main repository is more up to date than the one in the third party (this is the "gtksourceview3" package), so would that mean that the main repository won't be overruled?
That is correct. You can run 'sudo apt-get upgrade' and you shouldn't see 'gtksourceview3' in the list of upgradeable packages.

> And the lightdm in the third party ppa is more up to date than the main one, so I don't know if that one is stable.
It's hard to say, as the Ubuntu developers don't officially test packages from ppa's. But if you have the ppa enabled and the ppa version is more recent and the system can also retrieve the necessary dependencies it will try to update the package. 

I like your original plan - only update the ppa package you are intested in.

You can always do it another way:
Enable the PPA.
Run 'sudo apt-get update'
Run 'sudo apt-get install liferea liferea-data'
Disable the ppa.

I would expect that this package doesn't get updated that often, so trying to automate things could very well be more trouble than it's worth.

---

### Post by Bramkaandorp on 2012-06-05
> **drs305 said:**
> That is correct. You can run 'sudo apt-get upgrade' and you shouldn't see 'gtksourceview3' in the list of upgradeable packages.


It's hard to say, as the Ubuntu developers don't officially test packages from ppa's. But if you have the ppa enabled and the ppa version is more recent and the system can also retrieve the necessary dependencies it will try to update the package.

that's clear enough. Thanks.

> I like your original plan - only update the ppa package you are intested in.

You can always do it another way:
Enable the PPA.
Run 'sudo apt-get update'
Run 'sudo apt-get install liferea liferea-data'
Disable the ppa.

I would expect that this package doesn't get updated that often, so trying to automate things could very well be more trouble than it's worth.

I could do that, but the thing with ppa's is that they are meant to update on a regular basis, so one doesn't have to install the packages from the website.

For al intents and purposes, if I were to disable the ppa after updating, I might as well install the package from the ppa website, without adding the ppa itself.

---

### Post by drs305 on 2012-06-05
Per our discussion, here is a way to add a cron job which will check the liferea repository daily and update liferea and liferea-data if it finds new packages. It does this by temporarily adding the kampka repository, looking for updates for liferea and liferea-data and installing them if found. Then it removes the repository by putting back on your Desktop (or wherever).

Change the *paths and filename* as desired.

[LIST=1]
[*]Create a bash script to run daily. Create a new file (*myscript.sh* with this content (name it whatever you want):
> #!/bin/bash
mv */home/username/Desktop*/kampka-ppa-precise.list /etc/apt/sources.list.d/
apt-get update
apt-get install -y liferea liferea-data
mv /etc/apt/sources.list.d/kampka-ppa-precise.list */home/username/Desktop/*
apt-get update
exit 0
[*]Make the script executable:
```
sudo chmod +x *~/Desktop/myscript.sh*
```
[*]Add the job to cron
```
sudo sh -c "echo '@daily root */home/username/Desktop/myscript.sh*' >> /etc/crontab"
```
[/LIST]

Off on a business trip but will check back late tomorrow.

---

### Post by Bramkaandorp on 2012-06-05
I don't know exactly what went wrong, but it doesn't work.

I couldn't execute the first command, because the terminal doesn't recognise "sudo +x" (its words), so I simply ticked the "executable" boxes in the settings of the file. Might that be the problem?

Any way, when I start Ubuntu, it doesn't show anything different.

In the end, I decided to add the ppa as is, since the "lightdm" package isn't too far off the mark, and the other package isn't up to date at all, so not of any concern.

I'm still curious for future cases though, so I won't change the status to "solved" just yet.

---

### Post by drs305 on 2012-06-05
> **Bramkaandorp said:**
> I don't know exactly what went wrong, but it doesn't work.

I couldn't execute the first command, because the terminal doesn't recognise "sudo +x" (its words), so I simply ticked the "executable" boxes in the settings of the file. Might that be the problem?

Any way, when I start Ubuntu, it doesn't show anything different.

In the end, I decided to add the ppa as is, since the "lightdm" package isn't too far off the mark, and the other package isn't up to date at all, so not of any concern.

I'm still curious for future cases though, so I won't change the status to "solved" just yet.

I dropped the 'chmod' while I was typing. The command is corrected but making it executable is what was required (and you did it via GUI).

The script will run daily, but at what time I don't know. You probably wouldn't see it running even when the script works. It doesn't require any user input and may very well run completely in background.

You could check the /var/log/auth.log via Log File viewer to see if the commands ran as root.

---

### Post by Bramkaandorp on 2012-06-05
> **drs305 said:**
> I dropped the 'chmod' while I was typing. The command is corrected but making it executable is what was required (and you did it via GUI).

The script will run daily, but at what time I don't know. You probably wouldn't see it running even when the script works. It doesn't require any user input and may very well run completely in background.

You could check the /var/log/auth.log via Log File viewer to see if the commands ran as root.

In other words, I should have been more patient.

Do I have to undo anything if I remove the script from my desktop?

---

### Post by drs305 on 2012-06-05
> **Bramkaandorp said:**
> Do I have to undo anything if I remove the script from my desktop?

```
gksu gedit /etc/crontab
```
Remove the @daily line at the bottom of '/etc/crontab'. You can then do what you want with the script you created, as it won't be referenced anywhere - like it never happened.

---

### Post by Bramkaandorp on 2012-06-06
> **drs305 said:**
> ```
gksu gedit /etc/crontab
```
Remove the @daily line at the bottom of '/etc/crontab'. You can then do what you want with the script you created, as it won't be referenced anywhere - like it never happened.

Thanks!

---

