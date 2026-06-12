---
title: "Error when check for update!"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by lovevn on 2013-03-14
Recently, I have found that my Software Update is in problem. I show this:
[ATTACH=CONFIG]240164[/ATTACH]
Then I try to click "check" button and then it shows:
[ATTACH=CONFIG]240163[/ATTACH]
When I open terminal to type:
```
sudo apt-get update
```
result has some error:
> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found


and finally:
```
W: Failed to fetch http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```
How can I do to solve this problem? help me, thanks!

---

### Post by schragge on 2013-03-14
I guess you solved your problem on yourself as the thread is already marked [SOLVED]. If not, here is how:
```
sudo add-apt-repository -r ppa:norsetto/ppa
``` There's no packages for precise in that PPA, so it should be removed.

---

### Post by lovevn on 2013-03-14
> **schragge said:**
> I guess you solved your problem on yourself as the thread is already marked [SOLVED]. If not, here is how:
```
sudo add-apt-repository -r ppa:norsetto/ppa
``` There's no packages for precise in that PPA, so it should be removed.
Yeah, thank you so much! Sorry, I have a confusion when I choose title :">

---

