---
title: "Medibuntu repositories have moved..."
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by bapoumba on 2007-06-11
... to a new site, [http://www.medibuntu.org]("http://www.medibuntu.org").
Please check the instructions on their [howto page]("http://www.medibuntu.org/repository.php") or on the [wiki page]("https://help.ubuntu.com/community/Medibuntu").
The previous address ([http://medibuntu.sos-sts.com]("http://medibuntu.sos-sts.com")) is still working, for now ;)
Update your sources.list!
Reference:
[http://mrpouit.tuxfamily.org/index.php/post/2007/06/11/Medibuntuorg-tout-de-meme]("http://mrpouit.tuxfamily.org/index.php/post/2007/06/11/Medibuntuorg-tout-de-meme") (in French).

---

### Post by Kobalt on 2007-06-11
Thanks for the heads up Bapoumba ! ;)

---

### Post by bapoumba on 2007-06-11
Hey Kobalt :)
De rien !

---

### Post by Sp4rKy on 2007-06-12
After many days of configuration, medibuntu.org is now opened.

You can get information about what you **have to change** in your repository configuration at [http://www.medibuntu.org](http://www.medibuntu.org) :D

There is 4 lists that you can join, they are available at [http://lists.medibuntu.org/mailman/listinfo](http://lists.medibuntu.org/mailman/listinfo) (a general discussion list, a bugs related, an announcement list and a technical discussion list)

Feel free to join #medibuntu on freenode if you need more explanations 





Medibuntu.sos-sts.com will stay available during some weeks, so don't forget to change your configuration before we remove it :)


Contact, info, donation at [http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by Enverex on 2007-06-12
You may want to fix your howto on the site then, adding the repos like it says adds:

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by Sp4rKy on 2007-06-12
As i said, medibuntu.sos-sts.com isn't the good site now, it's medibuntu.org .
Anyway, i think we'll redirect it today :)

---

### Post by Enverex on 2007-06-12
> **Sp4rKy said:**
> As i said, medibuntu.sos-sts.com isn't the good site now, it's medibuntu.org .
Anyway, i think we'll redirect it today :)

... I know it's not, I was pointing out that your HowTo on the site downloads and installs an apt-repo list that use the old address!

---

### Post by bapoumba on 2007-06-12
W00t Sp4rKy!
Merged your thread in here :-þ

---

### Post by Sp4rKy on 2007-06-12
helooo bapoumba ,
no pb :þ until people show it :)

---

### Post by ricardisimo on 2007-06-12
Enverex makes a good point... the source list is still the "sos" repos, not the new one. Also, what's with the recommendation to report bugs to Launchpad, when the packages state quite clearly "This is Medibuntu and so these packages might be illegal... DON'T report bugs." Or words to that effect. Any idea what the sources.list entry should/will look like, and if the public key I got via the other method will still work? Thanks in advance.

---

### Post by bapoumba on 2007-06-12
> **ricardisimo said:**
> Enverex makes a good point... the source list is still the "sos" repos, not the new one. 
Are you both talking about _your_ sources.list ?
I browsed through all the pages before I posted them, to make sure the info was correct.

You have to edit the sources.list to direct to the proper repos.
Please paste the output to ```
cat /etc/apt/sources.list
```

---

### Post by Sp4rKy on 2007-06-12
* On medibuntu.org website, all page / files ahs been updated with new urls .
* On medibuntu.sos-sts.com, the page is still outdated, but we'll put an advert / a redirection 
* Indeed, you must NOT report bug *to ubuntu* , it can be explained clearfully :)
* For your source.list, go to medibuntu.org :D

---

### Post by mr_pouit on 2007-06-12
> **ricardisimo said:**
> Enverex makes a good point... the source list is still the "sos" repos, not the new one. Also, what's with the recommendation to report bugs to Launchpad, when the packages state quite clearly "**This is Medibuntu and so these packages might be illegal... DON'T report bugs**." Or words to that effect. Any idea what the sources.list entry should/will look like, and if the public key I got via the other method will still work? Thanks in advance.

No, this is not accurate:
>  This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!
 .
 Please report any bug to our bug tracker instead:
  [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)

And this warning is here to prevent people from reporting bugs for our packages to Ubuntu (and so give extra work to the bugsquad team ;))

[+] ok, Sp4rKy has been faster :-P

---

### Post by Sp4rKy on 2007-06-12
> **mr_pouit said:**
> 
[+] ok, Sp4rKy has been faster :-P

One time again ... :tongue:

---

### Post by ricardisimo on 2007-06-12
Sorry about that I guess I assumed that Launchpad and Ubuntu were one and the same.

I followed the instructions on the new medibuntu site, and it worked like a charm (merci Bapoumba), but absolutely no change was made to /etc/apt/sources.list. I'm assuming that there are several ways to subscribe to repositories, some of which don't read from sources.list. Is this true?

---

### Post by ricardisimo on 2007-06-12
Ah-Hah! I just noticed that it's in the subfolder. Never mind.

---

### Post by Sp4rKy on 2007-06-12
yes, i guess you've download an additional sources.list and store it in /etc/apt/sources.list.d :)
Anyway, check than medibuntu.sos-sts.com is removed fro your /etc/apt/sources.list if ti was .

---

### Post by ricardisimo on 2007-06-12
> **Sp4rKy said:**
> yes, i guess you've download an additional sources.list and store it in /etc/apt/sources.list.d :)
Anyway, check than medibuntu.sos-sts.com is removed fro your /etc/apt/sources.list if ti was .

I see... They can't compete with one another? Thanks again for everything.

---

### Post by Sp4rKy on 2007-06-12
what another ?
Even if you have both medibuntu.org and sos-sts.com, you shouldn't have any problem, as they use the same repo, and so both are updated.
Anyway, when we'll stop medibuntu.sos-sts.com, you'll get errors :)

Hope it's what you've asked for ...

---

### Post by ricardisimo on 2007-06-12
Yes, I just needed to know if the two repositories (medibuntu.sos-sts.com & medibuntu.org) were somehow at odds with each other or if one of them was simply going to die eventually. It's the latter. Thanks again.

I'm seeing in Update Manager Medibuntu-only version of k3b, one that apparently rips and burns encrypted DVDs, and yet I can't select it. This is obviously off-topic for this thread, (my apologies to all) but would you know if I need to remove my current k3b in order to install this other? Thanks.

---

### Post by Enverex on 2007-06-12
> **bapoumba said:**
> Are you both talking about _your_ sources.list ?
I browsed through all the pages before I posted them, to make sure the info was correct.

You have to edit the sources.list to direct to the proper repos.
Please paste the output to ```
cat /etc/apt/sources.list
```

NO!

Good god, how many times does it need to be said.

We went to the NEW SITE USING YOUR LINK.
Pasted the commands it says to add the repo for Feisty and when checking the file it added to sources.d/ it lists the OLD REPO which you said wont be operating for too much longer.

Is that CLEAR ENOUGH NOW?

---

### Post by Pumalite on 2007-06-12
> **Enverex said:**
> NO!

Good god, how many times does it need to be said.

We went to the NEW SITE USING YOUR LINK.
Pasted the commands it says to add the repo for Feisty and when checking the file it added to sources.d/ it lists the OLD REPO which you said wont be operating for too much longer.

Is that CLEAR ENOUGH NOW?

This is the code that I typed in my Terminal to get things done ( it all worked ):

sudo su -c 'echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free >> /etc/apt/sources.list'
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by Sp4rKy on 2007-06-13
@Enverex : There is 2 ways to use medibuntu repository : first, to add 'by hand' the line to sources.list , or , to get a sources part and to put it in /etc/apt/sources.list.d
If you used one of this solution the first time (with medibuntu.sos-sts.com) and the other the next time  (with medibuntu.org), you will get the 2 repositories in 2 locations.

I'll check again, all the files at medibuntu.org use *medibuntu.org adress

---

### Post by Enverex on 2007-06-13
> **Pumalite said:**
> This is the code that I typed in my Terminal to get things done ( it all worked ):

sudo su -c 'echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free >> /etc/apt/sources.list'
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

That is exactly what I did about 5 minutes after the thread was made about the server change. I've not used Medibuntu before so I shouldn't have duplicate repos (and I checked, I don't).

---

### Post by Sp4rKy on 2007-06-13
if you only did
```

sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

without have used Medibuntu before, you **can't** have a /etc/apt/sources.d/feisty.list as you don't downloaded it ...

---

### Post by Enverex on 2007-06-13
Actually you're right, it wasn't what the other user posted. Regardless I copy and pasted what was under the Fiesty howto part of the site at the time.

---

### Post by Sp4rKy on 2007-06-14
OK, so all is good now :)
Just have fun with Medibuntu :)

---

### Post by ricardisimo on 2007-06-14
This is odd... on one comp the previous commands added a repo to etc/apt/sources.list, while on the other, as I said earlier, it added to the sources.list in the subfolder etc/apt/sources.list.d. Can I just comment out the one in the subfolder, and add the appropriate lines in etc/apt/sources.list? Is there any compelling reason to have two separate lists? Thanks.

---

### Post by Sp4rKy on 2007-06-14
Indeed, you don't need to have both subdirectory file and line in /etc/apt/sources.list .
You can remove /etc/apt/sources.list.d/feisty.list if you have the line in the global /etc/apt/sources.list .

This is just use o avoid 'poluate' the official file with non official repository. But the 2 way do exactly the same thing

---

