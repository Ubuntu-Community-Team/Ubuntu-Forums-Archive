---
title: "Downgrade Perl 5.10 to 5.8.8"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by T0N3 on 2008-05-15
Hi,

I've somehow upgraded my default installation of Perl 5.8.8 to Perl 5.10. The only thing that I think could have done this was my installation of the perl module "Carp"

So what I'd like to do is downgrade Perl 5.10 back to 5.8.8.

Does anyone out there have any ideas?

---

### Post by AcidHawk on 2008-05-15
Perhaps this will help it does talk about xserver-xorg-core but I am sure you could do the same with Perl

[http://ubuntuforums.org/showthread.php?t=252921]("http://ubuntuforums.org/showthread.php?t=252921")

I think the key is something like 
```
sudo apt-get install perl=5.8.8.-12
```

---

### Post by T0N3 on 2008-05-15
I've just tried that now and I get the message "perl is already the newest version".

After seeing that I thought I'd be clever and try to reinstall Perl from Synaptic. It went through successfully but it made no difference. 

I also tried running:

```
sudo update-alternatives --config perl
```
and I just got a message "No alternatives for perl"

---

### Post by Rallg on 2008-05-15
Is the reason you wish to downgrade Perl, because you have a server (Apache) with web pages that call 5.8.8, and you don't want to re-write them to call 5.10?

If that is the only reason, you may be able to copy the Perl5.10 executable, and paste with name Perl5.8.8. Then, pages calling 5.8.8 will "find it" even though 5.10 is actually in use.

I had to do something similar with an earlier version of Perl. It worked.

---

### Post by T0N3 on 2008-05-15
Not quite. The reason is that I do a lot of development work in Perl 5.8.8 so the problem comes in when I compile my code, the dll's that are out in production are all for 5.8.8 so if ever I want to change any of that code I'll have to update the dll's as well. 

Also everyone that I work with also uses 5.8.8 so they would also have to update to 5.10 in order to do any changes to my code.

---

### Post by AcidHawk on 2008-05-16
Have you replaced perl 5.8.8 or do you simply have 2 versions of perl on your machine.  Perhaps there is just a path issue.

something that you could set with update-alternatives?

can you find all executable files called perl and then with the path before each one run perl -v

Something like
```

/usr/bin/perl -v
-or-
/usr/local/share/perl/bin/perl -v

```

Perhaps they will show different versions.

---

### Post by T0N3 on 2008-05-16
I've already tried update alternatives and that didn't help me but your post did get me thinking if perl 5.8.8 has been replaced or if the path has just changed so I ran

```
/usr/bin/perl -v
```
and it shows Perl 5.8.8 so I then ran

```
/usr/local/bin/perl -v
```
and I get Perl 5.10.0.

So that mean that my question has now changed to how do I now change the path where my pc is looking for Perl?

---

### Post by Frasco_1275 on 2009-06-23
hi TON3, did you solved your problem with perl 5.8 and how?

---

### Post by Friqenstein on 2009-10-12
Hello all,

I'm officially bumping this thread because I too have come across the broken perl package, unknowingly, with my recent change from HH8.04 to JJ9.04 after buying a new laptop.
It seems that Perl 5.10 has many bugs/issues one of which basically cripples everybody's pre-existing code/programs.

In short, I'm calling for the Ubuntu team to setup something that allows us to downgrade back to 5.8.x because lets face it, Perl 5.10 is obviously not ready.

[http://perlguru.com/gforum.cgi?post=37590;search_string=no%20event%20type%20or%20button%20%23%20or%20keysym;guest=5016637#37590](http://perlguru.com/gforum.cgi?post=37590;search_string=no%20event%20type%20or%20button%20%23%20or%20keysym;guest=5016637#37590)
This, among many other threads, out line one of the bugs/issues.
The reason I'm asking for the Ubuntu team to give us a downgrade option, besides perl 5.10 being broken, is because doing it manually is just a royal pain in the rear. Not to mention I've only found 1 site so far that shows the process in which to attempt the downgrade.

It's not only the Intrepid distro, because I'm running Jaunty 9.04 which I've recently installed on my new laptop. My old laptop was running Hardy Heron 8.04 and it had perl 5.8 which is where I wrote all of my previous perl code.

Long story short, we need a simple way to remedy this problem and it shouldn't have users resorting to CLI compiling which, lets face it, goes against the grain of what Ubuntu is all about.

At any rate, those of you who wish to attempt the downgrade yourself, here is the link to the site that I've found:
[http://www.perlmonks.org/index.pl?node_id=784595](http://www.perlmonks.org/index.pl?node_id=784595)

Hope this helps whomever needs it. I'm personally not going to fudge around with it right now because I'm in a remote location and cannot get descent access to download the older version.
Hopefully I'll be able to do this once I get home, or perhaps Ubuntu will have it fixed shortly.
Surely they could add a way to do it with Synaptic.

Regards,

---

### Post by hobleyd on 2010-03-29
This just bit me in a big way - for some reason Ubuntu 8.04 upgraded perl to 5.10 which fundamentally broke Zimbra 6.03. Grrr.

Anyway, I used this command to downgrade perl:

# apt-get install perl=5.8.8-12 perl-base=5.8.8-12 perl-modules=5.8.8-12 ucf libmx4j-java libldap-2.4-2 python2.5 debconf cdebconf

note the packages ucf, libmx4j-java, libldap-2.4-2, python2.5, debconf and cdebconf were needed to keep apt-get happy, but I don't think they actually changed much. This did result in a bunch of packages getting removed (mainly openoffice related it seems), but that was not an issue for me.

Don't forget to hold back the later perl modules so the next upgrade doesn't kill the perl install again:

# for p in perl perl-base perl-modules; do echo "${p} hold" | sudo dpkg --set-selections; done

---

### Post by irfans on 2011-04-21
Could anyone fix this problem?
 I am using Ubuntu 10.04 and the default PERL available is 5.10.
 Need to downgrade it to 5.8.8. Do we have a repository so that we 
 could get 5.8.8?

---

### Post by can.gungor on 2011-08-30
Hi all
I need downgrade my perl 5.10 to 5.8.8
I use ubuntu 11.04
please help. Im getting crazy.

---

