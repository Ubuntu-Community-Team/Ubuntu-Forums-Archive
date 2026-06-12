---
title: "Problem for run mayavi python script on Ubuntu Lucid"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by greenchiliishot on 2012-09-19
I install mayavi2 with the package manager and try to run mayavi python script on Ubuntu 10.04.4 LTS.
The script look like this:
```

    # Create the data.
    from numpy import pi, sin, cos, mgrid
    dphi, dtheta = pi/250.0, pi/250.0
    [phi,theta] = mgrid[0:pi+dphi*1.5:dphi,0:2*pi+dtheta*1.5:dtheta]
    m0 = 4; m1 = 3; m2 = 2; m3 = 3; m4 = 6; m5 = 2; m6 = 6; m7 = 4;
    r = sin(m0*phi)**m1 + cos(m2*phi)**m3 + sin(m4*theta)**m5 + cos(m6*theta)**m7
    x = r*sin(phi)*cos(theta)
    y = r*cos(phi)
    z = r*sin(phi)*sin(theta)
    
    # View it.
    from mayavi import mlab
    s = mlab.mesh(x, y, z)
    mlab.show()

```
The version of ipython is
`Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) `

The mayavi version is: `Mayavi 3.3.0`

I try every solution given in the help of mayavi website [mayavi website]("http://docs.enthought.com/mayavi/mayavi/mlab_running_scripts.html#running-mlab-scripts") but nothing work.
I get the error message:

    In [1]: run demo.py
    ---------------------------------------------------------------------------
    ImportError                               Traceback (most recent call last)
    
    /home/bob/demo.py in <module>()
        10 
        11 # View it.

    ---> 12 from mayavi import mlab
         13 s = mlab.mesh(x, y, z)
         14 mlab.show()

    ImportError: No module named mayavi
    WARNING: Failure executing file: <demo.py>

Please how it's possible to fix this ?

---

