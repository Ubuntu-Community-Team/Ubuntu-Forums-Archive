---
title: "Problem with Ubuntu Software Centre"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-03-15
Hello again. I wanted to download the Emerald Theme, but I get this notice from the Ubuntu Software Center. Obviously Emerald is safe, as thousands of people use it, so how can I get around this?

---

### Post by zvacet on 2011-03-15
Did you try to press OK button and install it?

---

### Post by TimmyK. on 2011-03-15
Yes. I hit OK, then it doesn't do anything.

---

### Post by kagerato on 2011-03-15
That message probably means the package is not cryptographically signed, or it is signed with an out-dated or revoked key.

Are you sure the repository you're getting this from is correct?  Emerald is in universe, and has been for a while.

You may be able to get more detailed (better) messages from a different package manager.  I recommend Synaptic.

Oh, and you didn't mention your Ubuntu version (nor the version of emerald you're trying to install).

In case you're wondering, keys for all apt-based package managers can be managed through the console program apt-key.  Normally, you don't ever do manual key management.  Feel free to read up on it (`man apt-key`), though.

The only likely reasons you would need to manually register a key would be (1) the package is far out-dated, or (2) the package is from an unknown third-party repository.

I would highly recommend against trying to force it through an override, or by disabling cryptographic verification.  The mechanism exists for security; otherwise just anyone could issue packages and claim they're from the official source.

---

### Post by TimmyK. on 2011-03-16
Sorry, but I didn't get a word of that. As I have told so many people before, I'm new, so don't assume I know *anything* about troubleshooting.

Now, it's not just doing that with emerald, but everything, even obviously trustworthy programs such as Mozilla Firefox. How can I get around this?

---

