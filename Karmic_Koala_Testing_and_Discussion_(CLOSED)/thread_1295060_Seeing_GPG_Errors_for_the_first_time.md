---
title: "Seeing GPG Errors for the first time"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mperry on 2009-10-19
From a karmic session today:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 
<ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I'm judging we need to get a new key to unlock the karmic door :-) I tried re-adding the medibuntu-keyring package as well and it still complains. I'll go to the "medi pad" and see what up.

---

### Post by renkinjutsu on 2009-10-19
i'm not getting gpg errors, but i DID start getting error messages about duplicates in my sources file, but that was easily fixed

nothing funny going on with my gpg keys though :confused:

---

### Post by mperry on 2009-10-19
> **renkinjutsu said:**
> i'm not getting gpg errors, but i DID start getting error messages about duplicates in my sources file, but that was easily fixed

nothing funny going on with my gpg keys though :confused:

Thanks! I just tried re-adding the ubuntu-keyring and it persists. Not sure what is up with the gpg errors.

---

### Post by mperry on 2009-10-19
Not a problem with the gpg keys it turns out. Just needed to vacuum and clean up the place a bit. All fixed up now. Sorry for the false report. If you get troubled by this, this is what fixed it for me:

[http://www.drewwithers.com/content/how-fix-ubuntu-gpg-error-badsig](http://www.drewwithers.com/content/how-fix-ubuntu-gpg-error-badsig)

After doing the required vacuuming and cleaning, karmic was happy again.

---

### Post by thecow on 2009-10-19
I get the following error when I run update:

"W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061"

Is this the same issue as you have described?

Edit:  Oh I see its something to do with Opera, strange

---

### Post by mcduck on 2009-10-19
> **thecow said:**
> I get the following error when I run update:

"W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061"

Is this the same issue as you have described?

Edit:  Oh I see its something to do with Opera, strange

No, your issue is that you have added a 3rd party repository but didn't add the signing key for that repository.

---

### Post by ronacc on 2009-10-19
I briefly got the GPG errors but just reloading the repos cleared it . The Oprea GPG error is probably because we are running Karmic which is still beta and Opera hasn't added that to the key yet . The latest they specificly point to is Jaunty ( which works fine ) , I've run into that before running alphas and betas .

---

