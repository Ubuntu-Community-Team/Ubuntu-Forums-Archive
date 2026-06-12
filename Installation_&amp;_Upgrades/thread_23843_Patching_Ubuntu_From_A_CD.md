---
title: "Patching Ubuntu From A CD"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by Cameron on 2005-04-04
I am wanting to apply ubuntu security packages to a machine that cannot connect to the internet via CD.

The Syanptic Help mentions being able to load the repositories from a CD.

I grabbed a few packages from the repository (following the links from the security - emails and put them on a CD.

When I told Syanptic to load the CD,  Syanptic came back with an error saying or meaning CD not created by apt-cd please use apt-cd to load.

I have had a look at the unoffical guide in the section about updating repositories manually and it wasn't very helpful in providing me with information for this situation.

How can I get Syanptic to load the CD?
Can I copy the packages over to the filesystem and then update the system from these local files?

---

### Post by ubuntu_demon on 2005-04-04
Read this :

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

for this to work you have to install dpkg-dev by :
sudo apt-get install dpkg-dev

The computer that you want to install the packes on has to have this line in its /etc/apt/sources.list :
```

deb cdrom:[name-of-the-cd]/ directory-name

```

Of course you have to do sudo apt-get update or hit refresh repositories in synaptic before you can actually use this cd-rom.

I haven't actually tried it. But please try it and report your results :)

---

### Post by Cameron on 2005-04-05
It Looks Like your suggestion will work. I just need to tweak a bit more to get it to actually do so.

So far
When I use a local repository ie file:\dir-on-local-system\ it works when I add the info for distrabution eg warty-security and the section.

I howeverget the error that the package.gz does not exist
(It requires me to get dpkg-dev as you said) :oops: 

Getting it is easy,
putting the file on the system is easy

*realising package.gz won't exist yet*
Will sudo apt-get install still work for dpkg-dev  on the system or Do I need to install it manually :?: 

_Reading from CD_

When I enter the line to read from the cdrom It still won't work (I have the packages located in a directory one level up from the root with a space in it
The Directory is  **[COLOR=Blue]Ubuntu USN[/COLOR] ** is the space after slash the important  in the code you wrote.

---

### Post by ubuntu_demon on 2005-04-05
[QUOTE=Cameron]It Looks Like your suggestion will work. I just need to tweak a bit more to get it to actually do so.

So far
When I use a local repository ie file:\dir-on-local-system\ it works when I add the info for distrabution eg warty-security and the section.

I howeverget the error that the package.gz does not exist
(It requires me to get dpkg-dev as you said) :oops: 

Getting it is easy,
putting the file on the system is easy

*realising package.gz won't exist yet*
Will sudo apt-get install still work for dpkg-dev  on the system or Do I need to install it manually :?: 

_Reading from CD_

When I enter the line to read from the cdrom It still won't work (I have the packages located in a directory one level up from the root with a space in it
The Directory is  **[COLOR=Blue]Ubuntu USN[/COLOR] ** is the space after slash the important  in the code you wrote.[/QUOTE]
 dpkg-dev is only necessary for the machine doing the packaging (it isn't necessary for the target machine)

"sudo apt-get install dpkg-dev" should work

---

### Post by Cameron on 2005-04-05
I only have the one Linux based machine so the **local repository** I want to create will be on the **machine without an internet connection**.  8-[ 

Is my idea still possible?

Is it possible to manually extract the dev-pkg.deb file with file roller or something and then create the packages.gz with that to have apt-get work after that  [-o<

---

### Post by Cameron on 2005-04-06
Looks Like I was a tad early with the last post.

I still have a problem though

I have the Packages.gz being created *[check]*
I also have the repository being queried *[check]*
I can therefore tell it to upgrade packages *[check]*

When I tell it to go and get it from the local repository
I says cannot down load and when I view the error message

it says cannot get 
> file:\apt-pkgs\security\\apt-pkgs\security\dists\warty\restricted\binary-i386\package-x

I can see the problem duplicated the \apt-pkgs\security\ of the directory structure
How can I remove it

Could it also be possible to get it to just have \apt-pkgs\security\ as the repository?

---

### Post by ubuntu_demon on 2005-04-06
[QUOTE=Cameron]Looks Like I was a tad early with the last post.

I still have a problem though

I have the Packages.gz being created *[check]*
I also have the repository being queried *[check]*
I can therefore tell it to upgrade packages *[check]*

When I tell it to go and get it from the local repository
I says cannot down load and when I view the error message

it says cannot get 


I can see the problem duplicated the \apt-pkgs\security\ of the directory structure
How can I remove it

Could it also be possible to get it to just have \apt-pkgs\security\ as the repository?[/QUOTE]
 What commands did you type before receiving the error ?

Why don't you include the enitre packages from the main tree instead of from the security tree ? You can still upgrade from those and probably will be easier to create. And recreating their directory structure isn't necessary.

---

### Post by Cameron on 2005-04-07
I've got apt looking and installing  successfully from the local directory    :grin:  

Your original post was enough

following the instructions of the linked document was enough when followed in the entirity.
 
I had to restart Syanptic to get it to install the packages though (just reloading the repsitory list was not enough)

Thanks for the help and the patience

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=Cameron]I've got apt looking and installing  successfully from the local directory    :grin:  

Your original post was enough

following the instructions of the linked document was enough when followed in the entirity.
 
I had to restart Syanptic to get it to install the packages though (just reloading the repsitory list was not enough)

Thanks for the help and the patience[/QUOTE]
 great !
np :)

---

