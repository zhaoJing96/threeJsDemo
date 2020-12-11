# threeJsDemo
Three.js 3D记载模型、绘制图形相关demo

##### GLTFLoader.html:导入GLTF模型
实现原理：GLTFLoader

##### eventGetPoint.html：点击事件获取点坐标
实现原理：通过监听鼠标点击获取与射线相交的对象数组
主要采用技术：Raycaster：这个类用于进行raycasting（光线投射）。 光线投射用于进行鼠标拾取（在三维空间中计算出鼠标移过了什么物体）。

##### drawLine.html：鼠标点击点绘制成线
实现原理：通过Raycaster获取点坐标，点坐标集合绘制线


### 动态绘制多边形本质是通过鼠标事件绑定和解绑来进行不同的图形绘制。平面绘制和立方体绘制不同，因为绘制多边形采用Shape生成二维形状，立方体绘制需要将最终图形旋转角度实现绘制。

#### 绘制多边形时，单击绘制第一个坐标点，在点击下一个点，下一次点击时将两个坐标点进行连接，鼠标双击后，调用绘制多边形的函数连接所有坐标点，绘制最终形成的多边形。
##### planeDrawShape.html:在平面绘制几何体
实现原理：点坐标集合绘制线，点坐标集合通过Shape转成形状，Shape形状绘制成几何体
主要采用技术：
Geometry
Line/LineLoop：绘制线
Shape：使用路径以及可选的孔洞来定义一个二维形状平面。
ShapeBufferGeometry/ShapeGeometry：从一个或多个路径形状中创建一个单面多边形几何体。

##### drawShape.html：在立方体上绘制几何体
实现原理：点坐标集合绘制线，点坐标集合通过Shape转成形状（二维坐标），通过ShapeBufferGeometry/ShapeGeometry将二维形状平面Shape绘制成几何体，由于二维坐标绘制和三围坐标系不同，需对生成几何体对象进行旋转即可
主要采用技术：
Geometry
Line/LineLoop：绘制线
Shape：使用路径以及可选的孔洞来定义一个二维形状平面。
ShapeBufferGeometry/ShapeGeometry：从一个或多个路径形状中创建一个单面多边形几何体。

#### 绘制圆时，鼠标点击选中圆心点坐标位置，监听鼠标移动mousemove事件来获取移动位置距离圆心点坐标的距离（两点之间距离），将该距离作为圆半径，最后鼠标双击生成圆形。
##### drawCircle.html：在立方体上绘制圆形
实现原理：点坐标确定圆心，通过鼠标移动确认半径(圆心和边缘点坐标距离)，通过CircleGeometry绘制圆

##### modelBlast.html：three.js记载3D模型，模型拆分爆炸效果，模型部件改变颜色
实现原理：gltfLoader加载模型，改变模型position实现爆炸添加TweenLite动画，改变模型材质color实现颜色改变