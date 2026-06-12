---
title: "Firefox 3 Beta 5 Update"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by thecorleonefamily on 2008-04-03
I just came to know that Firefox 3 Beta 5  has been released and it has various improvements. I would like to download this through Synaptic (and not run it through the archive the Firefox site gives), but it doesn't show up in Synaptic. Any suggestions?

I also tried:

```
sudo apt-get update
```
and
```
sudo apt-get install firefox
```

But it says no new version...

---

### Post by DoubleEweAreEx on 2008-04-04
I am in the same boat.
I downloaded the archive from Mozilla and found there was no installer.
Now I know if I just copy the files it will run, but I want to do this the correct way.

ie  Do I get rid of the Firefox 3.0b4 folder in /usr/lib? 
     How do I maintain the shortcut to FF still works?
     How do I make sure that when Firefox 3.0 is released I can install it neatly over my existing install.

Its a pain that Mozilla do not have better documentation on this for beginners :confused:

---

### Post by gsmanners on 2008-04-04
In Gutsy, you need to enable Backports, but they are only up to Firefox-3.0 beta 3.

I imagine beta 5 is on the way for us Hardy testers.

---

### Post by DoubleEweAreEx on 2008-04-04
Yeah I am running Hardy and its available.
Just need to know the correct process for installing?

---

### Post by Wobedraggled on 2008-04-04
I'd just wait for it to show up in the updates, shouldn't be long now.

---

### Post by tad1073 on 2008-04-04
The only problen with the beta's is that the extentions need to catch up.

---

### Post by mikewhatever on 2008-04-04
> **DoubleEweAreEx said:**
> I am in the same boat.
I downloaded the archive from Mozilla and found there was no installer.
Now I know if I just copy the files it will run, but I want to do this the correct way.

ie  Do I get rid of the Firefox 3.0b4 folder in /usr/lib? 

Well, yes, unless you want two betas.

     > How do I maintain the shortcut to FF still works?

If the shortcut points to the same place and a valid executable, it should still work. If it doesn't, delete it and create a new one. What's the big deal?

     > How do I make sure that when Firefox 3.0 is released I can install it neatly over my existing install.

What do you mean neatly? Would you still require guides after having installed two betas?

> Its a pain that Mozilla do not have better documentation on this for beginners :confused:

Perhaps, if you need step by step instructions beta software is not for you. I am quite sure Firefox3 will be provided by for Ubuntu after the final version is released.
Don't get me wrong, not trying to moralize. It's just seems like a good thing to remember, beta software is not intended for beginners.

---

### Post by Bablefish on 2008-04-04
I can tell you why those commands don't work, Offically the full release of a non beta version of Firefox 3 will come out this June. Why don't you just wait, besides the beta versions have some problems that won't be in the final release.

---

### Post by ccw on 2008-04-04
> **thecorleonefamily said:**
> I just came to know that Firefox 3 Beta 5  has been released and it has various improvements. I would like to download this through Synaptic (and not run it through the archive the Firefox site gives), but it doesn't show up in Synaptic. Any suggestions?

I also tried:

```
sudo apt-get update
```
and
```
sudo apt-get install firefox
```

But it says no new version...

Ubuntu developers haven't packaged it yet:

[https://launchpad.net/ubuntu/+source/firefox-3.0](https://launchpad.net/ubuntu/+source/firefox-3.0)

They're usually pretty quick about it. I'd imagine it will be available Monday, if not over the weekend.

---

### Post by DoubleEweAreEx on 2008-04-04
"Perhaps, if you need step by step instructions beta software is not for you. I am quite sure Firefox3 will be provided by for Ubuntu after the final version is released.
Don't get me wrong, not trying to moralize. It's just seems like a good thing to remember, beta software is not intended for beginners."

Yes, thank you Mike. I am well aware of this. I am not a beginner to software, merely a beginner to Linux. I am a systems engineer and I quite enjoy beta testing software.
I have used many Firefox betas on my windows boxes and want to do the same with my new linux install.

I find the best way to learn is to jump in with both feet and that is what I am doing with Linux.
Comments like yours are not really helpful, infact it comes across as elitist.

I am more than able to get 3,0b5 running, but as I am new to linux I did not want to jerry rig it if there are better/proper ways of installing it.

Thank you to everyone else btw.

---

### Post by DoubleEweAreEx on 2008-04-04
> **mikewhatever said:**
> What do you mean neatly? Would you still require guides after having installed two betas?

Perhaps I should just clarify one thing. 
My main query is based on the fact that each beta installs to a different folder. 
When ver 3 is released and I have 3.0b4 and 3.0b5 'installed' will it tidy up or would I need to manually clean up. I dont mind doing this, but if by installing/upgrading a particular this would be all automated I would rather do it that way.

Its really a matter of learning best practice not just 'making it work and shutting up'
Trying to learn here.

---

### Post by mikewhatever on 2008-04-07
I don't know for sure, but it would make sense if 3b5 overwrote 3b4 installation if both are installed from Ubuntu repositories. The same should apply to installing from tar.gzs downloaded from Mizilla site if you unpack to the same location overwriting the existing files. However, if you unpack to a different location, say, home directory, you'll end up with both 3b4 and 3b5.

---

### Post by DoubleEweAreEx on 2008-04-07
Yep, thats what it appears to do.
All good now.
Cheers

---

