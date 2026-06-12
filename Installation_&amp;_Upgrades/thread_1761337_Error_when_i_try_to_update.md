---
title: "Error when i try to update"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by chaosisme on 2011-05-18
i keep getting an error when i try to update my system. ive tried a few various things while browsing through the forums and none seem to help. my error is saying "E: Type 'N.B.' is not known on line 13 in source list/etc/apt/sources/list
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache>open()failed, please report" 

I'm still very new to Ubuntu.

---

### Post by Rubi1200 on 2011-05-18
Hi and welcome to the forums :-)

Sounds like a corrupted sources list may be the problem.

Go to the terminal and post the output of the following command please:

```
cat /etc/apt/sources.list
```

Paste the contents into a new post and then highlight all text and click on the # icon to wrap with code tags (it makes for easier reading).

Thanks.

---

### Post by Psychoscorpic on 2011-05-18
Hi Chaosisme

I had the same problem - do this in Terminal (I accidentally left off -vf, but it still worked, except moaned about trying to delete folder):
```
sudo rm /var/lib/apt/lists/* -vf
```
then
```
sudo apt-get update
```
The above should strip out the Sources list that is corrupt, then get fresh ones (takes some time). Auto-triggered my Update Manager into action, but you may have to start yours or Synaptic yourself.

Thanks to the following threads:
[http://ubuntuforums.org/showthread.php?t=1759681&highlight=E%3A_cache](http://ubuntuforums.org/showthread.php?t=1759681&highlight=E%3A_cache)
[http://ubuntuforums.org/showthread.php?t=1750755&highlight=E%3A_cache](http://ubuntuforums.org/showthread.php?t=1750755&highlight=E%3A_cache)

---

