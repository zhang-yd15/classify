�������㷨
1.Ԥ�⺯����predict function����������Ƶ�ģ�ͺ�������predict function(w, b) = w*x + b��w,bΪ����: 

 a1 = activation(w1*x + b1) 
 
 a2 = activation(w2 * a1+ b2) 
 
 predict function = a2 
 
 activationΪ�������һ��ΪʹĿ������Ի�����sigmoid(x) = 1/(1+e^-x)��ReLU(x) = max(0, x)

2.�������Ĳ�������w1,b1,w2,b2�ȣ����õ����ݶ��½�����������Back Propagation�㷨: 

w1 := w1 - rate*dw1 

w2 := w2 - rate*dw2 

b1 := b1 - rate*db1 

b2 := b2 - rate*db2 

������ֻҪ�ܺ���ļ��������ʹԤ�⺯����������ǰ���Ĳ�������

3.������ۺ���cost function��ʹ֮����С���� 
cost function = (1/m) * �ۼӷ���predict function(i) - y(i)��^2, i = 1,2,3,��,m.(mΪѵ����������

Back Propagation�㷨
����ѵ����{(x1, y1), (x2, y2), (x3, y3), �� ,(xm, ym)}, �Լ����Լ����������, ��L��
1.ǰ�򴫲��������ÿ�㵥Ԫal, �����x, w, b, a, z���Ǿ���xiΪѵ����(xi, yi), �磺 
a0 = xi��
z1 = w1 * x + b1; 

a1 = activation1(z1); 

z2 = w2 * a1 + b2; 

a2 = activation2(z2); 
�� 

zl = wl * al-1 + bl; 

al = activationl(zl); 
��. 

zL = wL * aL-1 + bL; 

aLi = activationL(zL)

2.����ÿһ�㵥Ԫ�����delta, yiΪѵ����(xi, yi), activationT(x)Ϊactivation(x)�ĵ���������: 

deltaL = aLi - yi; 

deltaL-1 = (wL.T * deltaL) .* activationL(aL-1); 

deltaL-2 = (wL-1.T * deltaL-1) .* activationL-1(aL-2); 
�� 

delta1 = (w2.T * delta2) .* activation2(a1)

3.��ÿһ�㵥Ԫ�����ݸ�����w,b, D��ʼ��Ϊ0, ����:
 
D1 = D1 + delta1 * a0.T = D1 + delta1 * x.T;
 
D2 = D2 + delta2 * a1.T; 

D3 = D3 + delta3 * a2.T; 
�� 

DL = DL + deltaL-1 * aL-1.T;

4.��1,2,3����m�κ󣬸��²���w,b, ����: 

w1 = w1 - rate * (1/m) * (D1 + lambda * w1); 

b1 = b1 - rate * delta1; 

w2 = w2 - rate * (1/m) * (D2 + lambda * w2); 

b2 = b2 - rate * delta2; 
�� 

wL = wL - rate * (1/m) * (DL + lambda * wL); 

bL = bL - rate * deltaL;







