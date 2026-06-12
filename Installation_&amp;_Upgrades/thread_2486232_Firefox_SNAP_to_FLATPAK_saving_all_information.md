---
title: "Firefox SNAP to FLATPAK saving all information"
date: 2023-04-23
forum: Installation &amp; Upgrades
---

### Post by ken-e-unix on 2023-04-23
Hi.

What's required when moving Firefox from a SNAP to a FLATPAK to save all user data like passwords, history, bookmarks, etc. ?

I am currently on Ubuntu 22.04.

Thanks

---

### Post by #&amp;thj^% on 2023-04-23
All I ever do is grab the whole .mozilla folder and copy it back after the Flatpak install.
Make a copy of that for safety sake.
EDIT: I feel I need to add this as well, The official solution for any Firefox profile migration is to sign up for a Mozilla account and use **_Firefox Sync_**. It's either that or copy that .mozilla profile around.

---

### Post by ActionParsnip on 2023-04-24
> **1fallen said:**
> All I ever do is grab the whole .mozilla folder and copy it back after the Flatpak install.
Make a copy of that for safety sake.
EDIT: I feel I need to add this as well, The official solution for any Firefox profile migration is to sign up for a Mozilla account and use **_Firefox Sync_**. It's either that or copy that .mozilla profile around.

+1

Backups are your friend

---

### Post by Holger_Gehrke on 2023-04-24
With the Snap version of firefox the '.mozilla' folder isn't a subdirectory of $HOME, instead it's in '~/snap/firefox/common/'. While this is probably due to some restriction imposed by snap (no access to hidden direct subdirectories of $HOME) it allows you to have separate configurations for a firefox snap and a firefox installed in another way.

Holger

---

### Post by ken-e-unix on 2023-04-24
Since ~/snap/firefox contains several folders:
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 2088
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 2154
drwxr-xr-x  4 ken ken 4096 Mar 22 09:03 2487
drwxr-xr-x  4 ken ken 4096 Apr 23 17:42 2579
And there is:
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 common
lrwxrwxrwx  1 ken ken    4 Apr 23 17:42 current -> 2579
Is there some procedure written that has the user 1) Install flatpak FireFox 2) Copy directories from ~/snap to ~/.mozilla 3) Tell the new Firefox which directory to use. I.E. 2579 ?
Thanks

---

### Post by ken-e-unix on 2023-04-25
Since ~/snap/firefox contains several folders:
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 2088
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 2154
drwxr-xr-x  4 ken ken 4096 Mar 22 09:03 2487
drwxr-xr-x  4 ken ken 4096 Apr 23 17:42 2579
And there is:
drwxr-xr-x  4 ken ken 4096 Dec 19 12:48 common
lrwxrwxrwx  1 ken ken    4 Apr 23 17:42 current -> 2579
Is there some procedure written that has the user 1) Install flatpak  FireFox 2) Copy directories from ~/snap to ~/.mozilla 3) Tell the new  Firefox which directory to use. I.E. 2579 ?
Thanks

---

### Post by BBQdave on 2023-04-25
> **ken-e-unix said:**
> Hi.

What's required when moving Firefox from a SNAP to a FLATPAK to save all user data like passwords, history, bookmarks, etc. ?

You could also create an account with Firefox. Then log in what ever version you are using with all information saved.

And not sure what you gain from Firefox Flatpak over Firefox Snap?

---

### Post by ken-e-unix on 2023-04-26
I was reading that SNAPS on Ubuntu are going away.

Nice baby snap...

Ken

---

### Post by tea for one on 2023-04-26
> **ken-e-unix said:**
> I was reading that SNAPS on Ubuntu are going away.
By any chance, was the date of the publication April 1st?

---

### Post by mendres82 on 2023-04-26
That actually was an april fools' joke, if I remember correctly.

---

### Post by ken-e-unix on 2023-04-26
Maybe your right:
Enough of it! Ubuntu to Ditch Snap Completely With 24.04 LTS Naughty Nightingale On this historic date, Canonical has  decided to abandon the Snap project and remove it completely in the  upcoming release of 24.04 codenamed Naughty Nightingale.
      [Abhishek]("https://news.itsfoss.com/author/root/") **April 1, 2023**  . 9:43 AM 2 min read
[https://news.itsfoss.com/ubuntu-ditch-snap/](https://news.itsfoss.com/ubuntu-ditch-snap/)

---

