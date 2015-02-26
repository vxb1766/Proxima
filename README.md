<h3>Hosted on GitHub - http://vxb1766.github.io/Proxima/</h3>
		<h6>Donot try to resize the window and check for responsiveness. Media queries are not present.</h6>
</h3><hr>
	I assumed few things when solving it. Firstly, The layout:
	<ol>
		<li>For the blue and pink color, It looked like google's material design color's. Hence I followed their color scheme. <a href='http://www.google.com/design/spec/style/color.html#color-color-palette'>Link Here</a></li>
		<li>The two div's that are most obvious are called <ol><li>desktopContainer</li><li>mobileContainer</li></ol>
		<li>There were several ways to separate them. I used float left for both and set Appropriate Margins</li><br>
		<li>The other approach I was thinking was to use an empty div as an separator. SO I would have 3 divs instead of two</li>
		<li>I did not find an iphone Image that I could superimpose on div2 and bring the text of mobile container to the front of the canvas as per ypu .pmd file</li><br>
		<li>The height of the elements were not present. Hence, I have padding/margin properties that try to mimic you'r pmd to the closest. So at the first glance it might seem as though desktopContainer layout far exceeds the requirement. However, it's still 95px from the bootom wrt it's parent</li><br>
		<li>Facebook icon is from font-awesome. I found thumbs-down, but it wasn't right handed. I checked for glyphicons in bootstrap and fontawesome but couldnt find righthanded one. I am assuming the right hand thumbs up is mirrored+rotated version of thumb's up left handed.</li><br>
		<li>Circular icons : border Radius is half the width & height.</li><br>
	</ol>
	<hr>
	<h3>Certain Hack's I am not proud of</h3>
	<ol>
		<li>The 32px between circular Icon's
			<ol>
				<li>No Matter how much I tried I could not set it to 32 px.</li>
				<li>So I used span element and used content 'aaai' this is 27px and automatic padding of 4 px are given and the total comes to 31px. This was the closest I could get to</li>
				<li>I tried used empty divs in between the images. That dint work either.</li>
			</ol>
		</li>
		<li>The spacing between the two div's:
			<ol>
				<li>I had issue with the MobileContainer. How do I set it to 215 px from desktopContainer <strong>and</strong>
					also 115px from right.
				</li>
				<li>For this I did a bit of math. 
					<ol>
						<li>Screen size : 1309px</li>
						<li>divContainer+mobileContainer+115px+215px+115px = 1151px</li>
						<li>1309px - 1151 = 158 px;</li>
						<li>I divided this by 2 and increased each div by 76. so I got an approximate 33%</li>
						<li>Once i figured out the width of each need's to be 33% I then changed desktopContainer to 35% and mobileContainer to 31%</li>
					</ol>
				</li>
			</ol>
		</li><br>
		<li>The same problem was present with mobileContainer too. I can have position relative to the parent and then use position = absolute for the child element and set bottom = 75 px or I can do the same for top. I could not understand how I could set the height of the div to satisy both top 65px and bottom 75px.</li><br>
		<li>To solve this issue, I used the following approach. Desktop Container is 95px from bottom  while mobileContainer is 75px from bottom. Since I had already done the math for desktopContainer, I just set the height of the mobile container to 20px more than whatever was the height of desktop container.</li><br>
		<li>For this I used jQuery. Since It was just one line of jQuery, I did not separate the script to a separate file.
		jQuery Used : <Strong>$(".mobileContainer")[0].clientHeight = $(".desktopContainer")[0].clientHeight+20; </strong></li>
		<br>
	</ol>
