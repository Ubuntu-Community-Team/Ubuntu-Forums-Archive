---
title: "Maya Font Installation Problem"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by xpawnrip on 2010-05-10
Hy
I saw this problem on other forums too but I didn't see the solution.
I installed Autodesk Maya 2008 on Ubuntu 9.10 Lucin Lynx and everything works fine except when i want to create text.
Creat->Text and i get the error:](*,)
// Error: Unable to open postscript font file for Courier // 
// Error: Unable to open postscript font file for Courier // 

And this is what the entire script editor displays:
file -f -new;
// ./untitled // 
commandPort -securityWarning -name commandportDefault;
// mental ray for Maya 9.0 
// mental ray for Maya: using startup file /usr/autodesk/maya/mentalray/maya.rayrc
// mental ray for Maya: setup
// mental ray for Maya: initialize
// mental ray for Maya: using 1 license
// mental ray for Maya: register extensions
// mental ray Node Factory: loaded
// mental ray for Maya: successfully registered
// mental ray for Maya: loading startup file: /usr/autodesk/maya/mentalray/maya.rayrc
// parsing /usr/autodesk/maya/mentalray/include/architectural.mi
// loading /usr/autodesk/maya/mentalray/lib/architectural.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/base.mi
// loading /usr/autodesk/maya/mentalray/lib/base.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/contour.mi
// loading /usr/autodesk/maya/mentalray/lib/contour.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/paint.mi
// loading /usr/autodesk/maya/mentalray/lib/paint.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/physics.mi
// loading /usr/autodesk/maya/mentalray/lib/physics.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/production.mi
// loading /usr/autodesk/maya/mentalray/lib/production.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/subsurface.mi
// loading /usr/autodesk/maya/mentalray/lib/subsurface.so
// generating Maya nodes...
// parsing /usr/autodesk/maya/mentalray/include/surfaceSampler.mi
// loading /usr/autodesk/maya/mentalray/lib/surfaceSampler.so
// generating Maya nodes...
updateRendererUI;
createNode makeTextCurves -n "textForBevel#";
// textForBevel1 // 
setAttr -type "string" textForBevel1.text "Test";
setAttr -type "string" textForBevel1.font "Courier";
createNode bevelPlus;
// bevelPlus1 // 
createNode styleCurve -n "innerStyleCurve#";
// innerStyleCurve1 // 
createNode styleCurve -n "outerStyleCurve#";
// outerStyleCurve1 // 
setAttr outerStyleCurve1.style 0;
setAttr innerStyleCurve1.style 0;
setAttr bevelPlus1.width 0.1;
setAttr bevelPlus1.depth 0.1;
setAttr bevelPlus1.extrudeDepth 0.25;
setAttr bevelPlus1.capSides 4;
setAttr bevelPlus1.numberOfSides 4;
setAttr bevelPlus1.tolerance 0.01;
setAttr bevelPlus1.normalsOutwards true;
setAttr bevelPlus1.polyOutUseChordHeight false;
setAttr bevelPlus1.polyOutUseChordHeightRatio false;
setAttr bevelPlus1.orderedCurves false;
createNode mesh;
// polySurfaceShape1 // 
connectAttr textForBevel1.outputCurve bevelPlus1.inputCurves;
connectAttr textForBevel1.count bevelPlus1.count;
connectAttr textForBevel1.position bevelPlus1.position;
connectAttr innerStyleCurve1.outCurve bevelPlus1.innerStyleCurve;
connectAttr outerStyleCurve1.outCurve bevelPlus1.outerStyleCurve;
connectAttr bevelPlus1.outputPoly polySurfaceShape1.inMesh;
sets -edit -forceElement initialShadingGroup polySurfaceShape1;
CenterPivot;
select polySurfaceShape1;
 int $intArr[] = `polyEvaluate -v`; int $numVerts = 0; if (size($intArr) > 0) $numVerts = $intArr[0]; if ($numVerts > 0) { polyCleanupArgList 3 { "0","2","1","0","1","0","0","0","0","1e-005","0","1e-005","1","0","0","-1","0" };
polyProjection -ch 1 -type Planar -ibd off -icx 0.5 -icy 0.5 -ra 0 -isu 1 -isv 1 -md z ;
select -r `listConnections -t "shape"`;
};
changeSelectMode -object;
// Error: Unable to open postscript font file for Courier // 
// Error: Unable to open postscript font file for Courier // 

I understand that maya is looking for fonts in a specific folder but i have no idea where this folder is located on the Filesyste.:-s
If anyone can tell me how to solve this issue,please help.I'm sure there are more people facing this problem.

Thanks

---

### Post by xpawnrip on 2010-05-11
anyone anything?

---

### Post by rambomaya on 2010-08-21
I realize it's been three months maybe you found the solution  already but i'll tell you anyway :). Create Text looks in "File System/usr/X11R6/lib/X11/fonts/Type1/" , create the path if it doesn't exist, you need Type1 fonts in "pfa" format not sure if Maya reads "pfb" format in Linux, hopefully it will help anyone who still looking for this problem.

---

