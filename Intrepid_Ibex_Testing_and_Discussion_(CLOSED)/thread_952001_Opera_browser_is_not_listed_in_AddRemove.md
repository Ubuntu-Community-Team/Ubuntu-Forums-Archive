---
title: "Opera browser is not listed in Add/Remove"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2008-10-18
I've noticed that the Opera browser (non-free) is not listed in the Add/Remove app.

It would be a shame to not include Opera as an option to download considering the fact that it's offered in a native 64-bit version that I've been using for a long time now and it works great in Ubuntu.

I didn't see the Intrepid build posted in the following directory and I think that is where it should be listed (not to mention that the versions of Opera that are available are far outdated):
[http://archive.canonical.com/ubuntu/pool/partner/o/opera/](http://archive.canonical.com/ubuntu/pool/partner/o/opera/)

You can download Opera currently from their website and get Opera for Ubuntu 8.04 Hardy Heron and Ubuntu 7.10 Gutsy Gibbon.

The version for 8.04 works perfectly with Intrepid and I have had no problems with compatibility. It would be simple to grab the debs and make them available through Add/Remove since they are already compiled and ready to go.

Does anyone know why it's not already listed or how to get it listed again?

---

### Post by snova on 2008-10-18
Probably because it's proprietary.

Putting it in multiverse/restricted might be possible, but you'd have to check the terms under which Opera is licensed.

Writing a script to automatically downloaded and install it (like for Google Earth) might be another possibility.

In the meantime, it's one of the few proprietary programs that can be downloaded in a nice, convienent .deb- for several versions of Ubuntu, even! I don't even know how many other distros they support, but I think it's quite an impressive list.

---

### Post by gjoellee on 2008-10-18
Opera is available from [www.opera.com](www.opera.com) as a .deb if you want it...

---

### Post by Npl on 2008-10-18
Doesnt seem like commercial apps get much care and love from canonical. You can easily add opera`s own repository and thus have up-to-date versions.

Just unpack the attacked zip and copy it to the right location, then install opera
> sudo install -m 644 opera.list /etc/apt/sources.list.d
sudo apt-get update && sudo apt-get install opera

---

### Post by snova on 2008-10-18
Neat. I didn't know they had a repository. Apparently Google has one too, I read that yesterday.

---

### Post by OrangeCrate on 2008-10-18
I don't happen to use Opera, but, I think it's usually available from the "Partner" repository. I just added that repository, and checking Synaptic, I see that Opera is available for installation.

---

### Post by kyleabaker on 2008-10-18
@all
I currently already have Opera installed. I always install and test the snapshot builds (test builds).

I just wanted to see why Opera was not being added by default to the Add/Remove application.

I haven't much use for manually adding the repository as I always test the unreleased versions and report problems back. It just surprises me that Opera was removed when they now have excellent support for 64-bit Ubuntu.

---

### Post by kyleabaker on 2008-10-18
> **snova said:**
> Putting it in multiverse/restricted might be possible, but you'd have to check the terms under which Opera is licensed.

Writing a script to automatically downloaded and install it (like for Google Earth) might be another possibility.

It would be great if it could be added in multiverse/restricted. I'll see what I can find out about the license.

A script would be a quick and easy fix, but I'm looking for a better approach to making it available to new users via Add/Remove.

---

### Post by OrangeCrate on 2008-10-18
^, ^^,

See my edited post. If you've added, and enabled the Partner repository, it's in Synaptic.

---

### Post by ronacc on 2008-10-18
you don't need a repository entry , if you run the release version of Opera ( I also run the developement snapshots ) it will notify you when a new version is available all by itself . You can also run BOTH the stable (release) and dev (snapshot) versions without them interfering with eachother by INSTALLING the release as a .deb and just unzipping the dev .bz2 version into its own dir in your /home and then running the dev version from term inside of its own dir with ./opera  .

---

### Post by Npl on 2008-10-18
> **OrangeCrate said:**
> ^, ^^,

See my edited post. If you've added, and enabled the Partner repository, it's in Synaptic.Do you have 32bit or 64bit Ubuntu?
Cause I have never seen a 64-bit Opera in Synaptics Repos... but I havent looked for a couple weeks.

---

### Post by OrangeCrate on 2008-10-18
> **npl said:**
> do you have 32bit or 64bit ubuntu?
Cause i have never seen a 64-bit opera in synaptics repos... But i havent looked for a couple weeks.

32

---

### Post by ronacc on 2008-10-18
the 64bit version is available here   [http://www.opera.com/](http://www.opera.com/)    just click on the free download button it will detect what distro and archetecture you are running and point you at the right d/l .

---

### Post by kyleabaker on 2008-10-18
I'm running 64-bit, so maybe the problem is that Opera isn't being shown available for 64-bit versions?

I've enabled Partner and still don't see it. So can people with 32-bit confirm that it's available while people with 64-bit don't have it available?

---

### Post by oldsoundguy on 2008-10-18
It may not be in add/remove, but it is in Synaptic as mentioned above.  I installed it from there as a back up browser.

and 64 bit is in beta

[http://www.opera.com/support/search/view/842/](http://www.opera.com/support/search/view/842/)

---

### Post by kyleabaker on 2008-10-18
> **oldsoundguy said:**
> It may not be in add/remove, but it is in Synaptic as mentioned above.  I installed it from there as a back up browser.

and 64 bit is in beta

[http://www.opera.com/support/search/view/842/](http://www.opera.com/support/search/view/842/)

That resource is outdated. The official 64-bit versions are available for Opera 9.60 from [http://www.opera.com/download](http://www.opera.com/download) (if you're running a 64-bit distro) so they are not beta anymore.

Opera never releases anything to the official download page unless it's final or explicitly says beta.

Also, I'm not finding it listed in synaptic. Maybe my my sources are messed up:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

^^is that right? They didn't all update properly when upgrading from Hardy a long time ago. I tried it with hardy since it's listed in the directory:
[http://archive.canonical.com/ubuntu/pool/partner/o/opera/](http://archive.canonical.com/ubuntu/pool/partner/o/opera/)

..but that didn't show it and neither does intrepid.

---

### Post by kansasnoob on 2008-10-18
> **OrangeCrate said:**
> ^, ^^,

See my edited post. If you've added, and enabled the Partner repository, it's in Synaptic.

+1!

But I always update to the newest version. Even though the "pop up" says 8.04 it works fine in 8.10.

Oops. missed that this was 64 bit!

---

### Post by oldsoundguy on 2008-10-18
So be it, but if the release of the 64 bit came out after the build was frozen, the 64 bit will not appear in the package manager until the NEXT release is out.  So you WILL have to get it at the Opera site.

IE: you can not get FF 3.0x in the GUTSY repositories.  If you want it you have to use Ubuntuzilla at the SoftPedia site.

You can, however get it in the Hardy repositories .. but you will not be able to get the 3.1 in Hardy since Intrepid will be released before 3.1 goes out of beta. And again, it will be available at Ubuntuzilla.

---

### Post by kyleabaker on 2008-10-18
> **oldsoundguy said:**
> So be it, but if the release of the 64 bit came out after the build was frozen, the 64 bit will not appear in the package manager until the NEXT release is out.  So you WILL have to get it at the Opera site.

IE: you can not get FF 3.0x in the GUTSY repositories.  If you want it you have to use Ubuntuzilla at the SoftPedia site.

You can, however get it in the Hardy repositories .. but you will not be able to get the 3.1 in Hardy since Intrepid will be released before 3.1 goes out of beta. And again, it will be available at Ubuntuzilla.

Opera 9.5 was released in early June with final versions of 64-bit Opera. 9.6 is new.
[http://my.opera.com/community/blog/opera-9-5](http://my.opera.com/community/blog/opera-9-5)

^^You partner repo _is_ configured for Intrepid, correct? I had to manually change mine to Intrepid after upgrating from Hardy. Just trying to make sure that it's correct.

---

### Post by OrangeCrate on 2008-10-18
> **kyleabaker said:**
> That resource is outdated. The official 64-bit versions are available for Opera 9.60 from [http://www.opera.com/download](http://www.opera.com/download) (if you're running a 64-bit distro) so they are not beta anymore.

Opera never releases anything to the official download page unless it's final or explicitly says beta.

Also, I'm not finding it listed in synaptic. Maybe my my sources are messed up:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

^^is that right? They didn't all update properly when upgrading from Hardy a long time ago. I tried it with hardy since it's listed in the directory:
[http://archive.canonical.com/ubuntu/pool/partner/o/opera/](http://archive.canonical.com/ubuntu/pool/partner/o/opera/)

..but that didn't show it and neither does intrepid.

The following is more for other people reading this thread, than you. I assume you know how to do this already.

To add the Partner repositories:

```
sudo gedit /etc/apt/sources.list
```

If you upgraded from Hardy, the Hardy Partner repositories will be commented out. Just duplicate the deb and the deb-src below them, substituting Intrepid for Hardy.

Here's how they should look:

Your correct on the first one:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

If you want to add the source code, it would look like this:

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

Save the file, and close.

Then, go to Software Sources, and check to be sure that deb is "checked". If you want the source code, check that box too.

---

### Post by ronacc on 2008-10-18
just wanted to add , after doing what OrangeCrate said , don't forget to reload your repos .

---

### Post by wgrant on 2008-10-18
> **oldsoundguy said:**
> So be it, but if the release of the 64 bit came out after the build was frozen, the 64 bit will not appear in the package manager until the NEXT release is out.  So you WILL have to get it at the Opera site.

IE: you can not get FF 3.0x in the GUTSY repositories.  If you want it you have to use Ubuntuzilla at the SoftPedia site.

You can, however get it in the Hardy repositories .. but you will not be able to get the 3.1 in Hardy since Intrepid will be released before 3.1 goes out of beta. And again, it will be available at Ubuntuzilla.

Opera lives in the partner repository, so it is not frozen after release like the rest of the archive.

As can be seen from [its Launchpad page](https://edge.launchpad.net/ubuntu/+source/opera), it hasn't yet been updated since Hardy, and is only available on i386.

---

### Post by kyleabaker on 2008-10-18
> **OrangeCrate said:**
> Here's how they should look:

Your correct on the first one:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

If you want to add the source code, it would look like this:

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


Those are correct, but I'm still not seeing anything listed for Opera in synaptic package manager after reloading sources.

What version are you seeing that is available?

---

### Post by kyleabaker on 2008-10-18
> **wgrant said:**
> Opera lives in the partner repository, so it is not frozen after release like the rest of the archive.

As can be seen from [its Launchpad page](https://edge.launchpad.net/ubuntu/+source/opera), it hasn't yet been updated since Hardy, and is only available on i386.

Thank you. This was the point that I was trying to get at for the entire time. :D

Who/how do we contact to get this updated to latest compatible versions for 32 and 64?

---

### Post by OrangeCrate on 2008-10-18
> **kyleabaker said:**
> Those are correct, but I'm still not seeing anything listed for Opera in synaptic package manager after reloading sources.

What version are you seeing that is available?

9.27-20080331.6hardy1

---

### Post by nanotube on 2008-10-18
> **oldsoundguy said:**
> 
IE: you can not get FF 3.0x in the GUTSY repositories.  If you want it you have to use Ubuntuzilla at the SoftPedia site.


just a note: ubuntuzilla doesn't live on softpedia, but rather on sourceforge:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by ronacc on 2008-10-18
see screenshots , just taken in my intrepid install .

---

### Post by oldsoundguy on 2008-10-19
> **nanotube said:**
> just a note: ubuntuzilla doesn't live on softpedia, but rather on sourceforge:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

sorry about the error!

---

### Post by kyleabaker on 2008-10-19
> **ronacc said:**
> see screenshots , just taken in my intrepid install .

I'm not sure what your point is..

You should be more specific. Yes I see build 2444, same as I have....after installing manually like anyone can do. What is you point about your screenshots though?

---

### Post by ronacc on 2008-10-19
look at the version # , the point is it is the latest 64bit opera (9.60) and it does show in synaptic ( although I got the .deb straight from opera ) .

---

### Post by plun on 2008-10-19
Just a precaution, all versions **below 9.60** includes rather nasty vulnerabilities

[http://secunia.com/advisories/32177/](http://secunia.com/advisories/32177/)

"Highly critical"

[http://www.opera.com/support/search/view/901/](http://www.opera.com/support/search/view/901/)
[http://www.opera.com/support/search/view/902/](http://www.opera.com/support/search/view/902/)

Download:
[http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by Npl on 2008-10-19
> **ronacc said:**
> look at the version # , the point is it is the latest 64bit opera (9.60) and it does show in synaptic ( although I got the .deb straight from opera ) .Every deb you installed shows in Synaptic. That doesnt help you though if you still have to install it (or if you want opera to be updated with the rest of the system).

---

### Post by ronacc on 2008-10-19
wheather you install Opera from synaptic via deb from tar.bz2 or by magic , it will notify you of updates when they become available regardless of the currency of ubuntus repos or the third party repos . As to installing it , yes you need to get the latest and greatest direct from Opera but is that such a great hardship ? Ubuntu has a rather strict policy about including "closed source " software .

---

### Post by Npl on 2008-10-19
Its no hardship, I doubt anyone in this thread has a problem installing Opera or asked for help on this.
You`re missing the point.

---

### Post by ronacc on 2008-10-19
perhaps I am missing the point .From long use of Ubuntu I have come to accept that not every app I might want will be available via synaptic even open source apps, especialy in the dev versions of Ubuntu which I habitualy run . I expect to have to hunt some things down and sometimes even "roll my own" . In regards to "closed source" propriatary packages I expect no help whatsoever from Ubuntu and am greatful for any that they do provide . I am a long time Opera fan (very long time) and would love to see it as the default browser , I also realse that that will happen 3 days after they start serving icecream in a very warm place .

---

### Post by wgrant on 2008-10-19
Ubuntu has nothing to do with packages in Canonical's partner repository. Launchpad erroneously shows them as part of Ubuntu, but they are not. They are Canonical's.

---

