---
title: "check for upgrade"
date: 2020-09-26
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2020-09-26
How do I check to see if an upgrade is available on my system?  I never seem to be able to remember this.  Currently running 20.04.
Thanks.

Caruso

---

### Post by TheFu on 2020-09-26
```
sudo apt update
```

On 20.04, after running that command above, there will be a message with the command to run should any packages be available for upgrades to get the list. Just have to read the output a few lines above the last line.

I patched this morning, that command isn't being displayed to me now.

---

### Post by Impavidus on 2020-09-26
Depending on your flavour, version and settings there may also be a pop-up or a notification in one panel or another.

---

### Post by deadflowr on 2020-09-26
For current package updates
```
apt list --upgradeable
```
works best if run after an apt update.
But can be run at anytime.

For release upgrades
```
do-release-upgrade -c
```
note since you're on 20.04 there won't currently be an upgrade yet.
(At least not until next month sometime...maybe)

---

### Post by carusoswi on 2020-09-30
> **deadflowr said:**
> For current package updates
```
apt list --upgradeable
```
works best if run after an apt update.
But can be run at anytime.

For release upgrades
```
do-release-upgrade -c
```
note since you're on 20.04 there won't currently be an upgrade yet.
(At least not until next month sometime...maybe)

I ran that last command and received the following message:

There is no development version of an LTS available.
To upgrade to the latest non-LTS development release set Prompt=normal in /etc/update-manager/release-upgrades.

I navigated to the suggested path but did not see that 'prompt' clearly displayed.
Any advice appreciated.  I would like to upgrade to the latest non-LTS development release.

Thanks for the replies.

Caruso

---

### Post by scriber on 2020-09-30
I just received a notice that an upgrade to 20.04.1 LTS was available, this was at 7 AM mountain time.
I was wondering when it was coming too but now it's finally here.

---

### Post by deadflowr on 2020-09-30
> I navigated to the suggested path but did not see that 'prompt' clearly displayed.
Any advice appreciated. I would like to upgrade to the latest non-LTS development release.
The Prompt= is at the very bottom of the file.
It should be the only thing uncommented in the file.
You should also run an apt update after you make the change.

The do-release-upgrade -c option is for checking stable releases,
as I stated there currently are no stable releases after 20.04 yet.
20.10 comes out next month.

If you want to run an upgrade to the development release
then you use the -d option
```
do-release-upgrade -d
```

---

### Post by rsteinmetz70112 on 2020-09-30
> **deadflowr said:**
> 
The do-release-upgrade -c option is for checking stable releases,
as I stated there currently are no stable releases after 20.04 yet.
20.10 comes out next month.


there is as of yesterday a 20.04 release for upgrade.
```

$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '20.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

---

### Post by deadflowr on 2020-09-30
> **rsteinmetz70112 said:**
> there is as of yesterday a 20.04 release for upgrade.
```

$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '20.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

Is that from 18.04 or 20.04?
20.04 and 20.04.1 are the same release.
I've never seen a release upgrade offered for the same release.
Upgrading from one point release to another can be achieved by doing regular updates.

---

### Post by ActionParsnip on 2020-10-01
What is the output of
```

lsb_release -a; uname -a

```
Thanks

---

### Post by rsteinmetz70112 on 2020-10-01
> **deadflowr said:**
> Is that from 18.04 or 20.04?
20.04 and 20.04.1 are the same release.
I've never seen a release upgrade offered for the same release.
Upgrading from one point release to another can be achieved by doing regular updates.

It's from 18.04 LTS to 20.04.1 LTS the hold has been released.

---

### Post by carusoswi on 2020-10-01
> **deadflowr said:**
> The Prompt= is at the very bottom of the file.
It should be the only thing uncommented in the file.
You should also run an apt update after you make the change.

The do-release-upgrade -c option is for checking stable releases,
as I stated there currently are no stable releases after 20.04 yet.
20.10 comes out next month.

If you want to run an upgrade to the development release
then you use the -d option
```
do-release-upgrade -d
```

Thank you.
Caruso

---

