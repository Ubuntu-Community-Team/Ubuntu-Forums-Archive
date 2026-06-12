---
title: "Update Errors"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by tanya_814 on 2010-06-01
Hi,

I would really appreciate some help with the following (I'm going to be very detailed!): 

A while ago, I had some updates regarding language packs (with languages that I will never use), but it didn't update completely. Now, every day, an icon that looks like an orange triangle with an exclamation mark on it appears. I click on that, it says I havn't updated since 41 days. I click on "Check" and it starts to download, then a box pops up and says:

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct." 

And the info about the specific error says:

"GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9Failed to fetch [http://apt.boxee.tv/dists/intrepid/main/binary-i386/Packages.gz](http://apt.boxee.tv/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages.gz](http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages.gz)  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead."

Then I close the error notice, close the update manager, and the icon disappears for about a day, and reappears the next day.

Now, I really don't care to get the updates it wants me to get. How do I simply stop it from showing me the error info without disabling the updating all together (because I know updates are important!)?

If anyone has any ideas, please let me know (in easy language--I'm no computer wiz, unfortunately.) Thank you in advance!!! :)

---

### Post by Boondoklife on 2010-06-01
Is this a outside ppa that it is trying to get to? If it is then you could just disable it under:
System -> Administration -> Software Sources -> Other Software

This is a list of all other sources for you applications, including ppas.

---

### Post by tanya_814 on 2010-06-01
I'm sorry, I'm very bad with computer language. What does 'ppa' mean?

The updates are basically 'language-pack-gnome-kw
                                    "          -kw-base
                                    "          -mai
                                    "          -mai-base
                                    "          -pap
                                    "          -pap-base
                                    "          -sa
                                    "          -sa-base'

I don't even know if that is helpful or not. haha

And when you say 'other software,' do you mean 'third-party software?'
If yes, there are 'ppa.launchpad' things in there. Should I deselect those?

---

