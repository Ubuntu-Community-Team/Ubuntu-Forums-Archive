---
title: "mozilla apps"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by DavidFourer on 2006-06-18
I just upgraded to Dapper. Flawless install and better hardware support than Breezy.

However, Mozilla Composer, a great web page creation tool, disappeared from my applications menu. apparently Ubuntu uses it's own builds of firefox and thunderbird, which is confusing. The Mozilla website is also confusing because composer is listed as part of Mozilla suite, while firefox and thunderbird are separate apps in the newest versions.

I suspected mozilla-composer was still installed, but not in the applications menu any more. I looked in /usr/lib at the varios mozilla flolders and searched my hardrive for a file/folder "composer"

I can go to Applications/add-remove and find firefox but not composer. I can go to sys/admin/synaptic package manager and find firefox and thunderbird but not mozilla composer. I have multiverse and universe repositories checked.

There is a sticky called "my recommended Dapper sources.list". I don't know if I need any of this. I forget how I installed mozilla-composer in Breezy, whether I downloaded it from the mozilla site or found it in a repository.

While I'm on the subject of Mozilla...   I found I could not open Adobe Acrobat files in firefox, so I tried to install an Adobe add-on, which I previously had in Breezy.  I found the download, upbacked the tar-gz file, and tried to run a file called "install" (text executable it says).  I'm not getting anywhere.  

Help appreciated.

Thanks for any help.

---

### Post by Mirrorball on 2006-06-19
There is Firefox, Thunderbird, and the Mozilla suite, which has a web browser, email client, composer, and possibly other components. Install the suite if you want the composer. It's already on my KDE menu though. Try:
```
mozilla-suite -edit
```
To open PDF files in Firefox with Acrobat Reader, you need to install acroread and mozilla-acroread with apt.

---

### Post by FredB on 2006-06-19
[QUOTE=DavidFourer]I just upgraded to Dapper. Flawless install and better hardware support than Breezy.[/QUOTE]

Good point.

[QUOTE=DavidFourer]
However, Mozilla Composer, a great web page creation tool, disappeared from 
my applications menu.[/QUOTE]

Try Nvu, its *"son"*. It is in multiverse repository.

[QUOTE=DavidFourer]
apparently Ubuntu uses it's own builds of firefox and thunderbird, which is confusing. The Mozilla website is also confusing because composer is listed as part of Mozilla suite, while firefox and thunderbird are separate apps in the newest versions.[/QUOTE]

It is a part of Mozilla Suite, but SeaMonkey is the only fully supported fork now. Mozilla Suite (aka 1.7.xx version is dead).

[QUOTE=DavidFourer]
I suspected mozilla-composer was still installed, but not in the applications menu any more. I looked in /usr/lib at the varios mozilla flolders and searched my hardrive for a file/folder "composer"[/QUOTE]

Logical. Answered by the other poster.

[QUOTE=DavidFourer]
I can go to Applications/add-remove and find firefox but not composer. I can go to sys/admin/synaptic package manager and find firefox and thunderbird but not mozilla composer. I have multiverse and universe repositories checked.[/QUOTE]

As I said a little up, Nvu is the son of Mozilla Composer, and main coder of Nvu is Daniel Glazmann, dad of Composer component in the old Suite.

[QUOTE=DavidFourer]
There is a sticky called "my recommended Dapper sources.list". I don't know if I need any of this. I forget how I installed mozilla-composer in Breezy, whether I downloaded it from the mozilla site or found it in a repository.[/QUOTE]

Maybe an official package in main or universe repository ?

[QUOTE=DavidFourer]
While I'm on the subject of Mozilla...   I found I could not open Adobe Acrobat files in firefox, so I tried to install an Adobe add-on, which I previously had in Breezy.  I found the download, upbacked the tar-gz file, and tried to run a file called "install" (text executable it says).  I'm not getting anywhere.  

Help appreciated.

Thanks for any help.[/QUOTE]

I think the answer is already given ;)

---

### Post by DavidFourer on 2006-06-19
Thanks for the info.  I see that acroread and mozilla-acroread are installed by the Dapper upgrade.  When I click a link to a pdf on the web, I get a blank screen.  When I first upgraded, I had to go to Edit/Preferences and select how I open links in another application (such as a link in an email).  Perhaps I have something blocked or a wrong setting.

Nvu was a snap to install.  Launches from App/Programming/NVU.  Thanks for the tip.

I'm getting an error message:
Could not load icon
Details: Icon 'mozilla.png' not found
It causes no harm but it popped up about 6 times during the install and now today when I ran Nvu.

---

