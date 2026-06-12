---
title: "aptitude - minimal list of explicitely installed packages"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by wkuballa on 2012-05-01
Hi Guys

I want to install a new 12.04 system and I would like to have pretty much the same software installed which I have now on my 10.04.  I think that this search function from aptitude delivers the list I am looking for:

aptitude search '?installed ?not(?reverse-depends(?installed))'

The way I understand the query language of aptitude, the above statement asks for "all installed packages which are not requested by any other installed package".

The result looks pretty much okay, I get 364 packages this way.  However, off these 364 packages are 23 packages which are marked "A" (automatic).


I have two questions for all you experts out there:

1) Is my understanding of aptiude's query language correct?

2) How can I have packages marked "A" when they are not required by any other package?


cheers,
Werner

---

### Post by oldfred on 2012-05-01
I do not know apitude, but someone posted this version.

Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

I have always used dpkg to get a list but that is 1300 to 1500 packages as it always includes the depends.

I have gone from 10.10 to 12.04 and know I do not want all the packages. List includes OpenOffice which is now LibreOffice and I am not sure what else changed. 

I was hoping to review kford's post and see if I could do it semi-automated.
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by wkuballa on 2012-05-01
Looks like oldfred confirmed my first question.  His search string is identical to:

aptitude search '?installed ?not(?automatic) ?not(?reverse-depends(?installed))'

I.e., the automatic installed packages are excluded from the result.  This means in my case that the result would not include the 23 packages marked with "A".

I am still puzzled about these installed "A" packages which are not required by any other packages.  Could it be that I may have used some other utility (which does not care about dependencies) to delete some packages?  Is it safe to delete this 23 packages?

What are your thoughts?

I will probably do a few tests with this before I retire my good old 10.04 :-)

---

