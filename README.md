# SSRS-Remove-Duplicates-From-Filter-Parameters
Code to remove duplicates from filter parameters in SSRS Reports

Public Shared Function RemoveDuplicates(parameter As Parameter) As String()
Dim items As Object() = parameter.Value
System.Array.Sort(items)
Dim k As Integer = 0
For i As Integer = 0 To items.Length - 1
If i > 0 AndAlso items(i).Equals(items(i - 1)) Then
Continue For
End If
items(k) = items(i)
k += 1
Next
Dim unique As [String]() = New [String](k - 1) {}
System.Array.Copy(items, 0, unique, 0, k)
Return unique
End Function
