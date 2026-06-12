---
title: "updating Amazon's video player"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by mulceber on 2012-05-26
I've been watching a lot of tv shows through Amazon Prime lately (since Netflix doesn't support Linux, they're basically our only option). Today though, when I tried to use their web-player (on firefox), I got a message saying it needed to update. I waited for the download bar to fill, and when it finished, it gave the following error:

"An error occurred and your player could not be updated. This is likely because your Flash Player or Browser needs to be updated. This update is required to play back this video."

I figured this was because flash has stopped providing linux updates, so I tried to use Amazon's player on both Chromium and Chrome and I got the same result. 

Does anyone know what I can do to get the necessary updates (or just bypass them and get the player to work anyway)?

ps. I realize in retrospect that this is probably the wrong forum for this thread. If anyone would care to move it, I'd be fine with that.
[I]
edit: figured it out. Feel free to delete this thread.[/I]

---

### Post by T_W on 2012-06-02
How did you resolve this?

---

### Post by mulceber on 2012-06-03
It's been a week or so since this happened, so my memory's a little foggy on where exactly I found the answer, but iirc, I used the terminal and input:

sudo apt-get install libhal1
sudo apt-get install hal

Then I restarted the browser. I'm not entirely sure if that's the one, but I think it is. Let me know.                        -M

---

### Post by c901906 on 2012-06-20
> **T_W said:**
> How did you resolve this?

For me, after 

```
sudo apt-get install libhal1
sudo apt-get install hal
```

I did this:

```
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2
```


Note: Please ignore OPs request to delete this thread.

---

### Post by iveand on 2012-08-01
YES!! Thank you!! Above instructions (including clearing cache) work!!

---

### Post by JamesFlamingo on 2012-10-31
Thanks you so much. I have been trying to get a descent streaming source for a week!:lolflag:

---

### Post by amosbadamos on 2012-11-24
FWIW, I have been working through this issue as well. I had google Chrome (not Chromium) on one of my laptops running Ubuntu 12.04. When I upgraded to 12.10 the Amazon videos worked fine with Chrome. However, after the flash player required an upgrade the grandfathered Chrome browser would no longer update. I ended up needing to switch to Chromium to resolve the issue. BTW, I tried installing hal on the chrome as well.

---

### Post by wcroyal on 2013-01-03
> **iveand said:**
> YES!! Thank you!! Above instructions (including clearing cache) work!!

+1 on this solution.  Simply installing hal for me did not work, but removing everything under ~/.adobe/Flash_Player did the trick.  Thanks!

---

### Post by StretchNate on 2013-10-20
> **c901906 said:**
> 

```
sudo apt-get install libhal1
sudo apt-get install hal
```

I did this:

```
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2
```



Worked great, thanks!

---

