---
title: "ccmake text interleaving error messages (Installing VisIt)"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by Christian_Butcher on 2013-11-07
Hi,

So I'm trying to to install VisIt, which is frequently going wrong, but this post regards a possibly general problem I'm having.
The CMakeLists.txt file for the VisIt source that I'm trying to install has a nice commented section under some IF loops, essentially to throw an error message to ccmake if you set VISIT_USE_PARALLEL (or something similar) to ON, and don't have a set MPI compiler. This makes plenty of sense, but either there was some oversight in the writing of the previous section aiming to call ${CMAKE_ROOT}/Modules/FindMPI.cmake (incidentally I didn't have a CMAKE_ROOT - I set this manually, but no error messages were thrown beforehand. I could find no statement setting it earlier in the CMakeLists.txt file, but perhaps this is set when cmake is called?) and it wasn't called, or else it sets all of my MPI_blah_blah variables, but doesn't then pass them into ccmake. However it happens, ccmake (with advanced toggled on) never gives me a VISIT_MPI_COMPILER (or whatever) variable to complete.

In order to try and fix this problem, I have tried both setting the VISIT_MPI_COMPILER setting in the CMakeLists.txt file, and also in a site-config file and linking it with -DVISIT_SITE_CONFIG="path to file". Whilst the file linked nicely, and in both cases I got my MPI compiler field, and ccmake stopped complaining about not having an MPI compiler set, when I use either of these 'solutions' my ccmake begins to look horrible.

Specifically, after the first time I hit c to configure each time I run ccmake, presumably what would be the error messages are shown overlapped/behind/covered by the variables to set. This makes both hard to read, since they interrupt one another.
I attach an image showing the problem. ccmake does continue to configure and allow me to generate a makefile, but invariably I run into problems which are hard to troubleshoot given that ccmake becomes difficult to read after each iteration of configuring.

Any help you can provide would be much appreciated.
Please ask for any further details if needed.

Christian[IMG]http://s23.postimg.org/5gx9xolcr/ccmake_text_problem.png[/IMG]

---

### Post by Christian_Butcher on 2013-11-07
Seemingly dragging the window either to or from the top/side of my screen to make it automatically resize fixes this. Repeated 3 times with different strange overlay/underlay/whatever (although all on the same ccmake source and build directories) and it cleared it each time.

---

