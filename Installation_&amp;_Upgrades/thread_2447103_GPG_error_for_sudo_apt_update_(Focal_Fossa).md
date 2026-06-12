---
title: "GPG error for sudo apt update (Focal Fossa)"
date: 2020-07-12
forum: Installation &amp; Upgrades
---

### Post by lolcoolkat on 2020-07-12
Getting the following error: Not really sure how to fix. I'm currently using 20.04 (Focal Fossa) and ive tried literally all of the commands I found when googling the error. I should note.. i'm running Ubuntu on Legacy mode... not sure if that matters. Any help is appreciated!


[LIST]
[*][COLOR=#333333]GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease: The following signatures were invalid: BADSIG 3B4FE6ACC0B21F32 Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>[/COLOR]

[*][COLOR=#333333]E: The repository 'http://archive.ubuntu.com/ubuntu focal InRelease' is not signed.[/COLOR]

[*][COLOR=#333333]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/COLOR]

[*][COLOR=#333333]N: See apt-secure(8) manpage for repository creation and user configuration details.[/COLOR]

[*][COLOR=#333333]W: GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease: The following signatures were invalid: BADSIG 3B4FE6ACC0B21F32 Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>[/COLOR]

[*][COLOR=#333333]E: The repository 'http://archive.ubuntu.com/ubuntu focal-updates InRelease' is not signed.[/COLOR]

[*][COLOR=#333333]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/COLOR]

[*][COLOR=#333333]N: See apt-secure(8) manpage for repository creation and user configuration details.
[/COLOR]
[/LIST]

---

### Post by lolcoolkat on 2020-07-12
I've also run **sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32 **however then I get the following error: Hash Sum mismatch

---

### Post by lolcoolkat on 2020-07-14
Bump!

---

### Post by deadflowr on 2020-07-15
To fix hash sum mismatches try to clear out the /var/lib/apt/lists directory and rerun sudo apt update.
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

It's not clear from the postings, but is the gpg error persistent even after running the add-key command in post #2?

Edit: It's also important to post all things and/or commands you've tried. In detail.
Without that, help provided may be useless or unhelpful as you might have already tried whatever is suggested.

---

### Post by lolcoolkat on 2020-07-15
@deadflowr yep tried that. Forgot to add that to my original post. That didn't fix it unfortunately.

---

