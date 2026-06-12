---
title: "Our company wants to put CPU and GPU package to 9.10 if possible"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilghiz on 2009-07-25
Hi,

our company Elegant Mathematics Ltd. uses Ubuntu last 3 years and want to contribute in Ubuntu for free as the respect to Ubuntu comunity.

We have several iterative linear system solvers: CG, BiCGStab, GMRES etc., implemented on CPU and GPU with massively parallel support, single/double/quad precisions, real/complex arithmetics, and these solvers were commercialized by Elegant Mathematics since 1992. We would like to provide important part of these solves (especially with CUDA GPU support) for free for all Ubuntu users.

I know that Ubuntu have already several similar packages like superlu, umfpack, but these packages do not support GPU computing. Using GPU we can improve up to 50 times computational speed achieving 250 GFlop/s on GTX 260, and our achievements are listed on NVIDIA Corporate site at [http://www.nvidia.com/cuda](http://www.nvidia.com/cuda) 

The questions:

1. how to proceed to be listed with this package in Ubuntu repository and at what repository we may expect to be listed?

2. can we provide only libraries and include files without access to source code, or it must be provided with sources?

3. to whom can I refer to proceed?

4. this package is ready now, can we expect if we will work fast, enter to the 9.10 release?

PS: I tried to read "ContributeToUbuntu" but cannot answer myself to questions above.

PPS: If my topic does not fit to the forum, please, advise me where I can post it?

Sincerely,

Ilgis Ibragimov
--
Dr. Ilgis Ibragimov
Vice-President
Elegant Mathematics Ltd.
Hanauer Muehle 2
66564 Ottweiler
Tel: +49 163 74 144 73
[http://www.elegant-mathematics.com/](http://www.elegant-mathematics.com/)

---

### Post by gnomeuser on 2009-07-25
[QUOTE=ilghiz;7675600
1. how to proceed to be listed with this package in Ubuntu repository and at what repository we may expect to be listed?

2. can we provide only libraries and include files without access to source code, or it must be provided with sources?

3. to whom can I refer to proceed?

4. this package is ready now, can we expect if we will work fast, enter to the 9.10 release?
[/QUOTE]

This is definitely not the right place, you should probably sign up for the ubuntu-devel mailing list and ask there, they will at least be able to guide you. However I will try to the best of my ability.

1. It sounds like the package is only suitable for the nonfree repo (multiverse) as it does not appear to come with source code under an approved license and it depends on nonfree technologies (CUDA depends on the propritary nvidia driver)

2. If you want it in the main repos (even universe) the code not only has to be available the license has to be approved as being open source. Multiverse can have non-free packages (such an example would be unrar)

3. I would go to the ubuntu-devel mailinglist, there aren't many actual developers around here nor people who can asses your contribution properly.

4. The feature freeze for Karmic is approaching quickly you may definitely have problems there. 

Regardless, go to the mailing list and you shall hopefully find the guidance you seek.

---

### Post by Hairy_Palms on 2009-07-25
Sounds like this might be put in the trusted partner repository

[http://www.canonical.com/services/packaging](http://www.canonical.com/services/packaging)

or try contacting canonical directly, theyll be able to give you a proper response

---

### Post by ilghiz on 2009-07-25
Dear Gnomeuser,

thank you for your kind answers! I already subscribed in the ubuntu-devel mailing list, but was not sure that I can post such a request there. According to your advise, I will repost my question on ubuntu-devel mailing list right now.

We can provide some parts of our packages with GPL license as well, but surely not for GPU (since they depends on CUDA technology).

Sincerely,

Ilgis

---

### Post by ilghiz on 2009-07-25
Dear Hairy_Palms,

thank you for your kind advise! I will try your suggested way as well.

Sincerely,

Ilgis

---

### Post by lean on 2009-07-25
You know, there are a forum for packaging right here:
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

---

