---
title: "Updates failing - Google Chrome"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-03-07
Hello everyone, I hope someone can answer this question for me. For the past few days each time I trying updating my Ubuntu system I get the following message.

Message I receive:

Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages

I did a search and found something that stated I should go to **Software and Updates** and uncheck this package, I did that but yet I continue to get this message.
Thanks in advanced..

---

### Post by Bashing-om on 2016-03-07
RobGoss; Hey ...

Known issue . For systems running 64 bit .

See: [http://ubuntuforums.org/showthread.php?t=2315941&p=13451268#post13451268](http://ubuntuforums.org/showthread.php?t=2315941&p=13451268#post13451268)

for this resolution.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by RobGoss on 2016-03-07
Hello Bashing-om, Thanks for the fast reply.

My system is a 32-bit not 64, and from what I have been reading the 32-bit is not supported any more so what should I do I only use Google chrome....

---

### Post by QDR06VV9 on 2016-03-07
Last week they dropped support for 32 bit Chrome(No More Chrome 32 bit) so it is telling you that no more security updates I believe there is a 32 bit Chromium out there.
But you will still need to Delete(Remove Chrome) and the source-list in /etc/apt/source list. 
Hope this Helps

---

### Post by slickymaster on 2016-03-07
> **RobGoss said:**
> Hello Bashing-om, Thanks for the fast reply.

My system is a 32-bit not 64, and from what I have been reading the 32-bit is not supported any more so what should I do I only use Google chrome....
The 32-bit build configurations for Chromium continues to be supported, so you can still use Chromium.

---

### Post by Bashing-om on 2016-03-07
RobGoss; Ouch !

Google dropped 32 bit support and pulled all the 32 bit stuff off their server(s) .

You will have to find you another 32 bit web browser that will suit your needs  as there will be no further updates for 32 bit softwares .

elseif: a 64 bit machine. install the 'buntu 64 bit edition.

[INDENT][INDENT]in the name of progress ???
[/INDENT][/INDENT]

---

### Post by RobGoss on 2016-03-07
Thanks guys but is [COLOR=#000000] Chromium as good as Google chrome I never used it?

And what's the best way to install [/COLOR][COLOR=#000000] Chromium on my Ubuntu system

Big thanks to you all for your help[/COLOR]

---

### Post by QDR06VV9 on 2016-03-07
[COLOR=#000000]Chromium is built on Chrome..so yes.
```
sudo apt-get install chromium-browser
```
to install it
Netflix will require some extra packages like this "chromium-widevine" && "pepperflash-nonfree" 
There are some site that show how but I will have to find them.
Here is one: [http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html](http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html)

[/COLOR]

---

### Post by howefield on 2016-03-07
> **runrickus said:**
> Chromium is built on Chrome..so yes.]

Wrong way round.

@RobGoss, This might help in terms of the differences between the two: [https://chromium.googlesource.com/chromium/src/+/master/docs/chromium_browser_vs_google_chrome.md](https://chromium.googlesource.com/chromium/src/+/master/docs/chromium_browser_vs_google_chrome.md) and in addition, there is no flash player or pdf viewer in Chromium by default (both easily "fixable").

Chromium is available from the Software Centre or your package manager of choice.

---

### Post by RobGoss on 2016-03-07
Oh ok I'll give it a try and see what works 

I guess I should remove Google chrome? what's the best way to completely remove it 

thanks so much

---

### Post by Bashing-om on 2016-03-07
Just wondering ......

If one were, in this instance, to ppa-purge google-chrome-stable would that revert to chromium ??

[INDENT]possible ?
[INDENT][INDENT][INDENT]that "might" happen
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by howefield on 2016-03-07
> **RobGoss said:**
> I guess I should remove Google chrome? what's the best way to completely remove it

```
sudo apt-get purge google-chrome-stable
```

should completely remove chrome, although you don't have to remove Chrome just to get Chromium. You can have both on the system quite happily.

---

### Post by slickymaster on 2016-03-07
> **Bashing-om said:**
> Just wondering ......

If one were, in this instance, to ppa-purge google-chrome-stable would that revert to chromium ??

[INDENT]possible ?
[INDENT][INDENT][INDENT]that "might" happen
[/INDENT][/INDENT][/INDENT][/INDENT]

Nopes, Bashing-om

---

### Post by Bashing-om on 2016-03-07
Welp; 


slickymaster: " Nopes, Bashing-om"
Was a thought .. recon the package management system is smart, real smart .....

[INDENT][INDENT]just not that smart
[/INDENT][/INDENT]

---

### Post by RobGoss on 2016-03-07
But if I continue to use Google Chrome isn't it a risk do to the fact there's no more support for the 32 bit version?.

---

### Post by howefield on 2016-03-08
> **RobGoss said:**
> But if I continue to use Google Chrome isn't it a risk do to the fact there's no more support for the 32 bit version?.

I guess so, the point I was making was that having it on your system didn't mean you couldn't install chromium.

Yes, best to remove Chrome. :)

---

### Post by RobGoss on 2016-03-08
Ok sounds good I will remove Chrome I can't see any reason to keep it. I'm really surprise Google stop support for it.

Thanks so much everyone

---

### Post by slickymaster on 2016-03-08
> **RobGoss said:**
> Ok sounds good I will remove Chrome I can't see any reason to keep it. I'm really surprise Google stop support for it.

Thanks so much everyone

See this: [https://productforums.google.com/forum/#!category-topic/chrome/discuss-chrome/windows-10/Stable/wrMB9YbD5vk](https://productforums.google.com/forum/#!category-topic/chrome/discuss-chrome/windows-10/Stable/wrMB9YbD5vk)

---

