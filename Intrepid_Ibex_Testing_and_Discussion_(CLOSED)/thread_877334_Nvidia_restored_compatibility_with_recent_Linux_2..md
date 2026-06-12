---
title: "Nvidia restored compatibility with recent Linux 2.6 kernels but i cant build the debs"
date: 2008-08-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by michaelfavia on 2008-08-01
NVidia have released a new driver update that supposedly fixes incompatabilities with the .26 kernel series. (Their notes, not my testing indicate this). The releases are available here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I have a general distaste for installing non .deb based installation scrips for the obvious reasons. I attempted to update source and build the debs locally with pbuilder but i am not having much luck. Attempted to use 'dch' to update the changelog and expected those changes in the version information to be propagated through to the build scripts but it seems like there is a missing step or two as the packages have different filenames in the "pkg0" area as well.

Alberto would you mind very roughly describing the part I am missing or rebuild this package with the new source so we can test its functionality on the legacy chipsets. Id be happy to help manage this section in the future if desired. Thanks, Michael

---

