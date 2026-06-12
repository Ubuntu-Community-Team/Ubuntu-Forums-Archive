---
title: "update problem"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by mehras1991 on 2011-09-15
hi all
I installed some apps & things I needed on my ubuntu yesterday, & after that, today when I'm trying to update, it gives me an error,I appreciate if someone can help me with that.
& specially if there's some where else I have to post or ask this question,cause I'm new to this forum.


> Failed to download repository information

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965, W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://www.geekconnection.org/remastersys/repository/karmic/Sources](http://www.geekconnection.org/remastersys/repository/karmic/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Toz on 2011-09-15
Hello and welcome to the fourms.

It looks like you've got a combination of natty, maverick and karmic entries in your sources file. Usually a recipe for disaster. What version of Ubuntu are you using?

Can you post back the contents of the file **/etc/apt/sources.list**?

Also, what files do your have in your **/etc/apt/sources.list.d** directory?

To do this graphically, run the "Software Sources" application, click on the "Other Software" tab and review the entries. Make sure they align with the version of ubuntu you are running. Uncheck the ones that aren't and research and include the appropriate version-specific ppas.

---

### Post by mehras1991 on 2011-09-16
> **Toz said:**
> Hello and welcome to the fourms.

It looks like you've got a combination of natty, maverick and karmic entries in your sources file. Usually a recipe for disaster. What version of Ubuntu are you using?

Can you post back the contents of the file **/etc/apt/sources.list**?

Also, what files do your have in your **/etc/apt/sources.list.d** directory?

To do this graphically, run the "Software Sources" application, click on the "Other Software" tab and review the entries. Make sure they align with the version of ubuntu you are running. Uncheck the ones that aren't and research and include the appropriate version-specific ppas.
I'm using ubuntu 11.04


I saw some package belong to maverick & karmic, I disabled them, but still I get the same error for updating, what should I do about those packages??

(both virtualbox &remastersys are running just fine. do I have to remove them & install another version?)

[COLOR="DarkRed"]/etc/apt/sources.list[/COLOR]

> 

**Canonical Partners**
Software packaged by Canonical their partners
--
**Canonical Partners** (Source Code)
Software packaged by Canonical their partners
--
**Independent**
Provided by third-party software developers
--
**Independent** (Source Codes)
Provided by third-party software developers
--
**[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty** free non-free
--
**[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty** free non-free (Source Code)
--
**[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty** free non-free
--
**[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty** free non-free (Source Code)
--
[COLOR="Blue"]**[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick** contrib[/COLOR]
--
[COLOR="Blue"]**[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick** contrib (Source Code)[/COLOR]
--
**[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty** contrib
--
[COLOR="Blue"]**[http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/**[/COLOR]
--
[COLOR="Blue"]**[http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/** (Source Code)[/COLOR]
--
**[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) natty** main
--
**[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) natty** main (Source Code)
[B]--
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty[/B] main
--
[B]--
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty[/B] main (source Code)
--
**Mediubuntu - Ubuntu 11.04 "natty narwal"** ([http://packages.mediubuntu.org/](http://packages.mediubuntu.org/) natty free non-free)
--
**Mediubuntu (source - Ubuntu 11.04 "natty narwal"** ([http://packages.mediubuntu.org/](http://packages.mediubuntu.org/) natty free non-free) (Source Code)
--
**[http://ppalaunchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppalaunchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty** main
--
**[http://ppalaunchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppalaunchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty** main (Source Code)
--
**[http://ppalaunchpad.net/sevenmachines/flash/ubuntu](http://ppalaunchpad.net/sevenmachines/flash/ubuntu) natty** main
--
**[http://ppalaunchpad.net/sevenmachines/flash/ubuntu](http://ppalaunchpad.net/sevenmachines/flash/ubuntu) natty** main (Source Code)
--
**[http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) natty** main
--
**[http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty** main
--
**[http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty** main (Source Code)



------------------------------------------------------

[COLOR="DarkRed"]/etc/apt/sources.list.d[/COLOR]

> dropbox.list
dropbox.list.save
ferramroberto-java-natty.list
ferramroberto-java-natty.list.save
mattaeus123-mrw-gimp-svn-natty.list
mattaeus123-mrw-gimp-svn-natty.list.save
medibuntu.list
medibuntu.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.save
team-bxmc-ppa-natty.list
team-xbmc-ppa-natty.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.save

---

### Post by varunendra on 2011-09-16
That's a common behaviour when you add custom repositories, ppa's etc., and, in my personal opinion, can be safely ignored as long as the related software works and you trust the source.

So far, remastersys does not have a dedicated package for natty, the karmik one is the latest, so it is okay to have it in the repo. In fact in natty, it may need (as I've witnessed a few times) to be downloaded and installed manually from [here]("http://www.geekconnection.org/remastersys/repository/karmic/").

For virtualbox, if it is default 'ose', it should be updated by automatically. But if it is the puel version, you can update the repository link from their [website]("http://www.virtualbox.org/wiki/Linux_Downloads"), as well as getting the gpg key.

---

### Post by Toz on 2011-09-16
> **mehras1991 said:**
> I saw some package belong to maverick & karmic, I disabled them, but still I get the same error for updating, what should I do about those packages??
How did you disable them? According to your sources.list file, they are still enabled. Lets try editing the file directly. Open a terminal window and type in the following:
```
gksudo gedit /etc/apt/sources.list
```
To comment out an entry, add a **#** to the beginning of the line. For example:
> [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
...would become
> #[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib

Then:
1. Comment out the 2 maverick virtualbox lines and the 2 karmic geekconnection/remastersys lines.Save the file and exit.
2. Back in the terminal window, execute the following two commands:
```

sudo mv /etc/apt/sources.list.d/team-bxmc-ppa-natty.list /etc/apt
sudo mv /etc/apt/sources.list.d/team-xbmc-ppa-natty.list.save /etc/apt

```
(this will remove that problematic entry).
3. Reload by running:
```
sudo apt-get update
```

If this returns with errors, post them back. If not, we can start fixing what we removed. But before we start that, lets see if we can get apt-get functioning again.

> (both virtualbox &remastersys are running just fine. do I have to remove them & install another version?)
After we fix the entries (next step), you may have new versions to upgrade to.

---

### Post by mehras1991 on 2011-09-16
> **varunendra said:**
> That's a common behaviour when you add custom repositories, ppa's etc., and, in my personal opinion, can be safely ignored as long as the related software works and you trust the source.

So far, remastersys does not have a dedicated package for natty, the karmik one is the latest, so it is okay to have it in the repo. In fact in natty, it may need (as I've witnessed a few times) to be downloaded and installed manually from [here]("http://www.geekconnection.org/remastersys/repository/karmic/").

For virtualbox, if it is default 'ose', it should be updated by automatically. But if it is the puel version, you can update the repository link from their [website]("http://www.virtualbox.org/wiki/Linux_Downloads"), as well as getting the gpg key.
thanks, so if there's any update from other sources, this error doesn't affect them to let me update, right??

I have one more common problem, any time I try to use compiz for cube desktop, my launcher bar & everything disappears, so I have to do the "unity --reset" to fix it, is there anyway to fix it & make it work? (oww & if it helps my hardware is 64 & ubuntu is installed by default as x86, how can I update to 64 OS?)

& also I use ubuntu on my laptop & not for work, how can I know "known issues" for latest ubuntu  beta (11.10) if I want to use it?? (I googled, but I couldn't find any answer)

---

### Post by Toz on 2011-09-16
Actually, the remastersys repository entry isn't working and needs to be fixed (as per the error message you're getting). Virtualbox has a natty-specific ppa you should be using. Also need to look into xbmc error message you're getting.

---

### Post by mehras1991 on 2011-09-16
> **Toz said:**
> Actually, the remastersys repository entry isn't working and needs to be fixed (as per the error message you're getting). Virtualbox has a natty-specific ppa you should be using. Also need to look into xbmc error message you're getting.
how can I delete xbmc from terminal?? I want to remove it but I can't find it in my apps list in software  center

---

### Post by varunendra on 2011-09-16
> **mehras1991 said:**
> thanks, so if there's any update from other sources, this error doesn't affect them to let me update, right?? - Right! :)

For other issues that are not related to the topic of this thread, you should open new threads with relevant topic. That way you'll get more relevant answers from possibly more capable members. Oh, before starting a new thread, you should also make a search to see if a similar one already exists. If it does, you may post your question there.

For testing 'Any' OS, virtual machines are the best and safest way. If you feel limitations in them and wish to try without those limitations (like reduced performance or non-availability of 3D hardware acceleration), then you may choose to go the dual-boot way. But that has the potential to corrupt booting in case something goes wrong during installation.

Onto your original problem- do as toz suggested in post #5. Commenting out (by adding #) irrelevant repository links (in other words - disabling them) will get rid of most (or possibly all) of the error messages during updates.

---

### Post by Toz on 2011-09-16
> **mehras1991 said:**
> how can I delete xbmc from terminal?? I want to remove it but I can't find it in my apps list in software  center
See point #2 from post #5 above. This will move it out of harms way.

---

### Post by mehras1991 on 2011-09-17
> **Toz said:**
> How did you disable them? According to your sources.list file, they are still enabled. Lets try editing the file directly. Open a terminal window and type in the following:
```
gksudo gedit /etc/apt/sources.list
```
To comment out an entry, add a **#** to the beginning of the line. For example:

...would become


Then:
1. Comment out the 2 maverick virtualbox lines and the 2 karmic geekconnection/remastersys lines.Save the file and exit.
2. Back in the terminal window, execute the following two commands:
```

sudo mv /etc/apt/sources.list.d/team-bxmc-ppa-natty.list /etc/apt
sudo mv /etc/apt/sources.list.d/team-xbmc-ppa-natty.list.save /etc/apt

```
(this will remove that problematic entry).
3. Reload by running:
```
sudo apt-get update
```

If this returns with errors, post them back. If not, we can start fixing what we removed. But before we start that, lets see if we can get apt-get functioning again.


After we fix the entries (next step), you may have new versions to upgrade to.
thank you, everything went alright
when I pres update from update manager there's no error, but when I do the > sudo apt-get update it gives me this at the end:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_non-free_binary-amd64_Packages)

now what??

---

### Post by varunendra on 2011-09-17
Yep, you do have duplicate entries. Look for these lines in your sources.list file:
> [http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free
--
[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free (Source Code)
--
[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free
--
[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free (Source Code)

Add # in the beginning of first two lines so they become like this:
> #[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free
--
#[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free (Source Code)
--
[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free
--
[http://Packages.mediubuntu.org/](http://Packages.mediubuntu.org/) natty free non-free (Source Code)

As for the GPG error, you need to get public key for it. Problem is - I don't know how :-k. Maybe Toz can shed some light on it.

By the way, ppa's are third party repositories which keep changing and are also not as trustworthy as official Ubuntu repositories. I usually ignore such 'PubKey' related errors, although it is recommended to add public keys whenever you add a third-party repository.

I never used to add public key for virtualbox until recently, and always got the same "No Public Key" error message. Regardless, the packages always worked without problems. I think it is just a security verification mechanism to verify the validity of the source of a package, which we can safely ignore if we trust the source. But that is my personal opinion which is not so mature. I would really appreciate a description/explanation of its importance by an expert, as well as how to get/add it for ppa's.

---

### Post by mehras1991 on 2011-09-17
> **varunendra said:**
> Yep, you do have duplicate entries. Look for these lines in your sources.list file:


Add # in the beginning of first two lines so they become like this:


As for the GPG error, you need to get public key for it. Problem is - I don't know how :-k. Maybe Toz can shed some light on it.

By the way, ppa's are third party repositories which keep changing and are also not as trustworthy as official Ubuntu repositories. I usually ignore such 'PubKey' related errors, although it is recommended to add public keys whenever you add a third-party repository.

I never used to add public key for virtualbox until recently, and always got the same "No Public Key" error message. Regardless, the packages always worked without problems. I think it is just a security verification mechanism to verify the validity of the source of a package, which we can safely ignore if we trust the source. But that is my personal opinion which is not so mature. I would really appreciate a description/explanation of its importance by an expert, as well as how to get/add it for ppa's.
well, thanx to you too
we're good now
now the last line would be:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965

which I think, Toz can help me with it better

---

### Post by Toz on 2011-09-17
Can you post back the contents of your /etc/apt/sources.list file? Something doesn't look right thats generating that error.

---

### Post by mehras1991 on 2011-09-17
> **Toz said:**
> Can you post back the contents of your /etc/apt/sources.list file? Something doesn't look right thats generating that error.
here you go

> # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
# deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
# deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

---

### Post by bapoumba on 2011-09-17
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
Please try :

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B725097B3ACC3965

```

---

### Post by mehras1991 on 2011-09-17
> **bapoumba said:**
> Please try :

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B725097B3ACC3965

```
I thought so, I had feeling about this thing


> gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by Toz on 2011-09-17
> [http://ppa.launchpad.net](http://ppa.launchpad.net) natty
is not a valid ppa entry.

sources.list looks good - must be one of the files in your /etc/apt/sources.list.d. Run the following command (it will list the contents of all of the files in /etc/apt/sources.list.d) so we can locate the culprit.
```
for f in /etc/apt/sources.list.d/*; do echo "->"$f; cat $f; done
```
Post back the results.

Can you also post back exactly what 
```
sudo apt-get update
```
returns?

---

### Post by bapoumba on 2011-09-17
Hmm, I tried before I posted to make sure I was not mixing up the key ID:
```
bapoumba@SonyBlue:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B725097B3ACC3965
[sudo] password for bapoumba: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys B725097B3ACC3965
gpg: requesting key 3ACC3965 from hkp server keyserver.ubuntu.com
gpg: key 3ACC3965: public key "Launchpad lffl" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
Any other issue with your internet connection?

---

### Post by mehras1991 on 2011-09-17
> Any other issue with your internet connection?

I'm not sure, but I don't think so, cause I stay on campus... (up till now I didn't see any blocked server related to ubuntu)

> ->/etc/apt/sources.list.d/dropbox.list
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) natty main
->/etc/apt/sources.list.d/dropbox.list.save
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) natty main
->/etc/apt/sources.list.d/ferramroberto-java-natty.list
deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty main
deb-src [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty main
->/etc/apt/sources.list.d/ferramroberto-java-natty.list.save
deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty main
deb-src [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) natty main
->/etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-natty.list
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty main
deb-src [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty main
->/etc/apt/sources.list.d/matthaeus123-mrw-gimp-svn-natty.list.save
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty main
deb-src [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) natty main
->/etc/apt/sources.list.d/medibuntu.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free #Medibuntu - Ubuntu 11.04 "natty narwhal"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free #Medibuntu (source) - Ubuntu 11.04 "natty narwhal"
->/etc/apt/sources.list.d/medibuntu.list.save
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free #Medibuntu - Ubuntu 11.04 "natty narwhal"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free #Medibuntu (source) - Ubuntu 11.04 "natty narwhal"
->/etc/apt/sources.list.d/sevenmachines-flash-natty.list
deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) natty main
->/etc/apt/sources.list.d/sevenmachines-flash-natty.list.save
deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) natty main
deb-src [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) natty main
->/etc/apt/sources.list.d/team-xbmc-ppa-natty.list
->/etc/apt/sources.list.d/tualatrix-ppa-natty.list
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty main
->/etc/apt/sources.list.d/tualatrix-ppa-natty.list.save
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty main

---

