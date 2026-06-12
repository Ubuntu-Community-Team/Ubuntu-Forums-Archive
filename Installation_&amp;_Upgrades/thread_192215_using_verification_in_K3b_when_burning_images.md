---
title: "using verification in K3b when burning images"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-06-08
Recently, I was burning an image of the Dapper Drake download using the K3b program and I set the verification flag to ON.

But when the burn had finished the verification did not take place.  

Are you supposed to be able to use this verification function when burning a **disc image** as opposed to just burning a file or directory to the disc ?

I can use a verification process/function when I burn these disc images on my M/S windows machine using Roxio Easy Creator program.

Thanks.

---

### Post by asimon on 2006-06-08
What format had the image? Verification works (here) for normal .iso images. But k3b can not verify bin/cue images, but a wishlist bug report for this is already filed upstream.

---

### Post by wpshooter on 2006-06-08
[QUOTE=asimon]What format had the image? Verification works (here) for normal .iso images. But k3b can not verify bin/cue images, but a wishlist bug report for this is already filed upstream.[/QUOTE]

It was the ISO images of the Dapper Drake 6.06 RELEASE.

---

### Post by asimon on 2006-06-08
[QUOTE=wpshooter]It was the ISO images of the Dapper Drake 6.06 RELEASE.[/QUOTE]
Did you use the k3b version of Breezy for that? Between the breezy version of k3b and the Dapper one there were a lot of fixes regarding verification. When I used k3b (current dapper version) to burn the Kubuntu 6.06 release the verification worked.

---

