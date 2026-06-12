---
title: "An alternative program for solid edge?"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by WrathofTux on 2011-09-28
Hi im wondering if there are any good alternatives for solide edge, since i now am using ubuntu and cant get solide edge to work here :<

---

### Post by Frogs Hair on 2011-09-28
There are a number of cad programs for Linux found with a quick search . Some of the programs are free and some are expensive . You would have to compare features and compatibility  if your interacting with other cad users in a work environment .

---

### Post by Gemnoc on 2011-11-11
Hi,

It's an old post, but if you're still following the replies...

There are a few CAD programs on Linux, and fewer are Open Source. Are you looking for FOSS programs or commercial ones?

I know of two commercial parametric apps running natively on Linux: one is NX (formerly Unigraphics), from Siemens PLM. It's Solid Edge's big brother, and its price is in the 5 figures. The other one is a Parasolid-based SolidWorks look-alike from a small Swiss developer, Graphite One. But it's not very good IMHO, and around €1500. The website has been down for the past few weeks.

As for FOSS software, none displays the level of functionality of Solid Edge at the moment. But FreeCAD is getting there. I firmly believe it's "our best hope" for an open source parametric CAD app. The upcoming v0.12 presents a very much usable (even if not complete) constraints-based sketcher along with basic modeling tools like extrude, cutout and revolve and loft. For now you can only work on parts, but work has already started on an assembly module. The GUI lacks many tools and features, but there's a rich feature set accessible through Python scripting.

There are many FreeCAD videos on YouTube, go check it out.

What FreeCAD lacks at the moment:
[LIST]
[*]In sketch mode, being able to constrain to external elements (part's edges, ...)
[*]A complete Drawing module (to produce "drafts" in Solid Edge vocabulary), at the moment you can create views but not dimension them; drawings can be exported to DXF to dimension in another software like QCad/LibreCAD)
[*]Easy reference elements creation (planes), this should be tackled in v0.13
[*]A reliable DXF importer/exporter, but it's being worked on
[*]An assembly module, but chances are it will get started in v0.13 (see the video link in [this forum topic](https://sourceforge.net/apps/phpbb/free-cad/viewtopic.php?f=10&t=1523&start=10#p12299), be advised this is a very early prototype)
[*]Advanced surfacing tools (this may take a long time)
[/LIST]


It's going to take years yet to see a complete feature set, but FreeCAD is already nice to use for small projects, even if you won't be as productive.

The other one is HeeksCAD. It's geared more toward CAM, and some find it difficult to get used to its GUI. Its a lot less ambitious in scope than FreeCAD.

Almost forgot, if you're interested in seeing how the FreeCAD development's coming along, there's no need to compile the source: I helped set up two separate PPA, one of them with automatic daily builds. Packages are available for all currently supported Ubuntu versions in 32 and 64-Bit. More info here:

[https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Download#Ubuntu_PPA_packages](https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Download#Ubuntu_PPA_packages)

FreeCAD's development has been slow over the years, but it's really picked up in the past year, as more people have joined the project.

P.S. I haven't mentioned other CAD*programs that are not parametric...

---

