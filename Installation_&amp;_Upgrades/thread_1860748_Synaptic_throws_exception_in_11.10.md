---
title: "Synaptic throws exception in 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by a8jr on 2011-10-15
Just upgraded to 11.10 a few moments ago. I hate the Software Center so I installed Synaptic. However, I can't find the System Administration menu, so I run Synaptic from terminal, but it throws a C++ exception, I believe

$ sudo synaptic
terminate called after throwing an instance of 'std::out_of_range'
what():  vector::_M_range_check
Abgebrochen

The last line is in German, means aborted

I've reinstalled synaptic for a few times,  apt-get clean, update, upgrade; but no luck.

Any idea why?

Also, where to find the update manager?

---

### Post by a8jr on 2011-10-16
Forget it, I deleted the entire configuration folder (every hidden folder in your home directory with "." as it's name first character) then the synaptic runs.

However it costed the configuration of everything. I lost my firefox addons, transmission bittorrent list (the data is still in my HDD, just the transmission "forget" which torrents are running), even Ubuntu doesn't know how to open a directory or to display window border (because it "forget" to use nautilus and metacity).

Yesterday, I've tweaked the computer for the whole day. Now everything is fine.

So folks, just don't mess up with the configuration folder. Case closed.

---

### Post by billstei on 2011-10-17
I am also getting this error when running synaptic:

terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted

This thread is marked "SOLVED" but I don't think trashing every config directory in the home folder is the solution I'm looking for.  What I can say is it's not the .synaptic folder, which I did remove.

---

### Post by Squizz00 on 2011-10-22
I also get the same exception:

xxx@yyyyy:~$ sudo synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check

This thread is not solved, in my opinion. Deleting all my hidden folders is not an option. There must be a better way, since the only thing I did, was updating to 11.10.

---

### Post by billstei on 2011-11-30
Workaround: Run the Universal Access program, then under the Seeing tab, turn the Screen Reader to "ON", then turn it immediately "OFF", then quit.  Synaptic should/might run okay now.

---

### Post by glastonbury on 2011-12-03
Thank you, billstei ... your workaround worked great!

---

### Post by simön on 2012-02-08
> **billstei said:**
> Workaround: Run the Universal Access program, then under the Seeing tab, turn the Screen Reader to "ON", then turn it immediately "OFF", then quit.  Synaptic should/might run okay now.

weired, it worked! ;-)

---

### Post by simiasota on 2012-03-30
Worked for me too.
ubuntu 11.10
linux 3.0.0-17-generic 64 bit

---

