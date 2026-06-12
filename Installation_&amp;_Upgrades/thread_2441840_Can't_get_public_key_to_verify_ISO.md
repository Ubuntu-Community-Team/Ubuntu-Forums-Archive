---
title: "Can't get public key to verify ISO"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by shmu26 on 2020-04-27
Hi, trying to verify the latest Kubuntu
I run 
[HTML]gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS
gpg: Signature made Thu 23 Apr 2020 16:33:56 IDT
gpg:                using RSA key D94AA3F0EFE21092
gpg: Can't check signature: No public key
[/HTML]

Then I run
[HTML]gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com --recv-keys D94AA3F0EFE21092
gpg: [don't know]: invalid packet (ctb=3e)
gpg: read_block: read error: Invalid packet
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
[/HTML]

What am I doing wrong

---

### Post by TheFu on 2020-04-27
Why not just download the SHA256sum file, run **sha256sum** path-to-kubuntu.iso and compare the outputs either manually or using **diff**?

---

### Post by shmu26 on 2020-04-27
> **TheFu said:**
> Why not just download the SHA256sum file, run **sha256sum** path-to-kubuntu.iso and compare the outputs either manually or using **diff**?

I did that already. So I know the iso I downloaded is complete and uncorrupted.  Now I want to verify the authenticity of the iso, meaning, that it came from canonical and not from a malcoder.

Don't people do that? Am I overly paranoid?

---

### Post by CelticWarrior on 2020-04-27
> **shmu26 said:**
> Am I overly paranoid?

If you downloaded it from the official website, I would say yes, you are.

---

### Post by mörgæs on 2020-04-27
If the sha256 or md5 hash value is correct then it doesn't matter from where the ISO comes. The preferred way to download is from a torrent.

I don't think I have ever heard of tampered-with Buntu ISO's.

---

### Post by TheFu on 2020-04-27
> **shmu26 said:**
> I did that already. So I know the iso I downloaded is complete and uncorrupted.  Now I want to verify the authenticity of the iso, meaning, that it came from canonical and not from a malcoder.

Don't people do that? Am I overly paranoid?

Guess I&#8217;d ask what would you do if the sha256 matches, but the gpg doesn't?    md5 isn't nearly as compelling since researchers have been able to generate files that to collide with specific md5 hashes.

I&#8217;m pretty paranoid too. There is a point where trust comes in.  Someone would need to hack the distro server, perhaps a number of mirrors, repackage the iso, modifying the built-in sha256sum and modifying both files on the distribution system. After being able to do that, seems like hacking into the system with the gpg signature tools wouldn't be hard.

OTOH, I&#8217;m happy that _someone_ is doing the gpg validation beyond what APT does with every package that gets installed.

---

### Post by shmu26 on 2020-04-27
I agree that it's a paranoid stance to check gpg, but Mint was hacked a few years ago and offered tainted ISOs for download. The hackers posted the checksum of the tainted ISO, since they owned the server anyway, so you would never know.

---

### Post by mörgæs on 2020-04-27
True but it lasted only a day before the breach was discovered. 
It's fine to do the hash sum testing but in general I would say that other risks are more important.

---

