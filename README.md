# honeybeex
Honeybee plugin for Grasshopper

### [API Documentation](http://ladybug-analysis-tools.github.io/honeybeex/doc/)

```python
# Here is a simple example on how to use the API
from honeybeex.radiance.sky.certainIlluminance import SkyWithCertainIlluminanceLevel
from honeybeex.radiance.recipe.gridbased import HBGridBasedAnalysisRecipe
from honeybeex.hbsurface import HBAnalysisSurface


pts = [(0, 0, 0), (10, 0, 0), (10, 10, 0), (0, 10, 0)]
vectors = [(0, 0, 1)]

# create the sky
sky = SkyWithCertainIlluminanceLevel(2000)

# create a Honeybee surface using vertices
hbsrf = HBAnalysisSurface("001", pts, surfaceType=None, isNameSetByUser=True)

# put an analysis recipe together
rp = HBGridBasedAnalysisRecipe(sky, pts, vectors, None, [hbsrf])

# write the files and runs the analysis
rp.writeToFile("c:\ladybug", "test")
rp.run(False)

# read the results
print rp.results
```
